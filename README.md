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