import java.util.*;

class PageTableEntry {
    int frameNumber;
    boolean valid;

    public PageTableEntry() {
        this.valid = false;
        this.frameNumber = -1;
    }
}
