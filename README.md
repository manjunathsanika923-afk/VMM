import java.util.*;

class PageTableEntry {
    int frameNumber;
    boolean valid;

    public PageTableEntry() {
        this.valid = false;
        this.frameNumber = -1;
    }
}
class SegmentTableEntry {
    int base;
    int limit;

    public SegmentTableEntry(int base, int limit) {
        this.base = base;
        this.limit = limit;
    }
interface PageReplacement {
    int replacePage(List<Integer> memory, int page);
}
}
Class FIFO implements PageReplacement {
    Queue<Integer> queue = new LinkedList<>();

    public int replacePage(List<Integer> memory, int page) {
        int victim = queue.poll();
        queue.offer(page);
        return memory.indexOf(victim);
    }
public void addPage(int page) {
        queue.offer(page);
    }
}
class LRU implements PageReplacement {
    LinkedList<Integer> lruList = new LinkedList<>();
public void accessPage(int page) {
        lruList.remove((Integer) page);
        lruList.addFirst(page);
    }
public int replacePage(List<Integer> memory, int page) {
        int victim = lruList.removeLast();
         int frame = memory.indexOf(victim);
        lruList.addFirst(page);
        return frame;
    }
}
class VirtualMemoryManager {
    PageTableEntry[] pageTable;
Map<Integer, SegmentTableEntry> segmentTable;
