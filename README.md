# Managing-member-Exeption-
package com.company;

import java.util.ArrayList;
import java.util.Scanner;

class Member {
    private String firstName;
    private String lastName;
    private int memberID;

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public int getMemberID() {
        return memberID;
    }

    public void setMemberID(int memberID) {
        this.memberID = memberID;
    }
}


public class Main {
    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner(System.in);
        ArrayList<Member> members = new ArrayList<>();

        while (true) {
            printLoop();
            int numberOfSwitch = scanner.nextInt();
            switch (numberOfSwitch) {
                case 1 -> {
                    System.out.println("PLease enter the name:");
                    String firstName = scanner.next();
                    if (firstName.length() == 0 || firstName.length() == 1)
                        throw new Exception("Member first name is null or has One Character...!!!");
                    System.out.println("Please enter the lastNme:");
                    String lastName = scanner.next();
                    if (lastName.length() == 0 || lastName.length() == 1)
                        throw new Exception("Member last name is null or has One Character...!!!");
                    System.out.println("Please enter ID:");
                    int memberID = scanner.nextInt();
                    boolean hasDuplication = false;
                    for (Member member : members) {
                        if (member.getMemberID() == memberID) {
                            hasDuplication = true;
                            break;
                        }
                    }
                    if (hasDuplication) {
                        throw new Exception("Duplicate Member(ID): ");
                    } else {
                        Member member = new Member();
                        member.setMemberID(memberID);
                        members.add(member);
                    }
                }
                case 2 -> {
                    System.out.println("Please enter the ID to Remove:");
                    int memberId = scanner.nextInt();
                    boolean hasRemoveMember = false;
                    for (int i = 0; i < members.size(); i++) {
                        if (memberId == members.get(i).getMemberID()) {
                            members.remove(i);
                            hasRemoveMember = true;
                            System.out.println("THE MEMBER:" + memberId + " REMOVED...");
                        }
                    }

                    if (!hasRemoveMember) {
                        System.out.println("No user removed!");
                    }
                }
                case 3 -> {
                    if (members.isEmpty()) {
                        throw new Exception("The Our List is Empty");
                    }else System.out.println("The List Size:" + members.size());
                }

                default -> System.out.println("PLease enter Valid Number>>>!!!");
            }
        }
    }

    public static void printLoop() {
        System.out.println("""
                1) ADD MEMBER:
                2) REMOVE MEMBER:
                3) MEMBER COUNT:
                please Enter Number:"""
        );
    }
}
