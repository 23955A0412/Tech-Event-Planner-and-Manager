# Tech-Event-Planner-and-Manager
##CODE
import java.util.*;

class Participant {
    String name;
    String email;

    public Participant(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public void display() {
        System.out.println("Participant: " + name + ", Email: " + email);
    }
}

class Event {
    String eventName;
    String date;
    String time;
    String venue;
    List<Participant> participants;

    public Event(String eventName, String date, String time, String venue) {
        this.eventName = eventName;
        this.date = date;
        this.time = time;
        this.venue = venue;
        this.participants = new ArrayList<>();
    }

    public void registerParticipant(Participant p) {
        participants.add(p);
        System.out.println(p.name + " has been registered for " + eventName);
    }

    public void showDetails() {
        System.out.println("\nEvent: " + eventName);
        System.out.println("Date: " + date);
        System.out.println("Time: " + time);
        System.out.println("Venue: " + venue);
        System.out.println("Registered Participants:");
        for (Participant p : participants) {
            p.display();
        }
    }
}

public class TechEventManager {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Enter Event Name:");
        String name = sc.nextLine();
        System.out.println("Enter Date (DD-MM-YYYY):");
        String date = sc.nextLine();
        System.out.println("Enter Time:");
        String time = sc.nextLine();
        System.out.println("Enter Venue:");
        String venue = sc.nextLine();

        Event techEvent = new Event(name, date, time, venue);

        while (true) {
            System.out.println("\n1. Register Participant\n2. Show Event Details\n3. Exit");
            int choice = sc.nextInt();
            sc.nextLine();  // Consume newline

            switch (choice) {
                case 1:
                    System.out.println("Enter Participant Name:");
                    String pname = sc.nextLine();
                    System.out.println("Enter Email:");
                    String email = sc.nextLine();
                    techEvent.registerParticipant(new Participant(pname, email));
                    break;

                case 2:
                    techEvent.showDetails();
                    break;

                case 3:
                    System.out.println("Exiting...");
                    sc.close();
                    return;

                default:
                    System.out.println("Invalid choice. Try again.");
            }
        }
    }
}
