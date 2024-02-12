# Array Of Object

```java
public class Student {
    public static void main(String[] args){
        Subject sb[] = new Subject[3];
        sb[0] = new Subject("s1", "Dhruv", 100);
        sb[1] = new Subject("s2", "Ratnoo", 100);
        sb[2] = new Subject("s3", "Bhawna", 100);

        for(Subject sub : sb){
            System.out.println(sub);
        }
    }

    static class Subject {
        private String subID;
        private String name;
        private int maxMarks;
        private int marksObtain;


        public String getSubID() {return subID;}
        public String getName() {return name;}
        public int getMaxMarks() {return maxMarks;}
        public int getMarksObtain() {return marksObtain;}

        public void setMaxMarks(int maxMarks) {this.maxMarks = maxMarks;}
        public void setMarksObtain(int marksObtain) {this.marksObtain = marksObtain;}

        public Subject(String subID, String name) {
            this.subID = subID;
            this.name = name;
        }
        public Subject(String subID, String name, int maxMarks) {
            this.subID = subID;
            this.name = name;
            this.maxMarks = maxMarks;
        }
        public Subject(String subID, String name, int maxMarks, int marksObtain) {
            this.subID = subID;
            this.name = name;
            this.maxMarks = maxMarks;
            this.marksObtain = marksObtain;
        }

        public String toString(){
            return "\nSubject Id: "+subID+"\nName: "+name+"\nMax Marks: "+maxMarks;
        }
    }
}

```
