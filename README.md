package kekthua;

import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Cha {
    protected String inputString;
    protected List<Integer> soList;

    // Phương thức nhập ngẫu nhiên một chuỗi có cả chữ và số
    public void nhapNgauNhien() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Nhập chuỗi (bao gồm cả chữ và số): ");
        inputString = scanner.nextLine(); // Chuỗi ngẫu nhiên có cả chữ và số
        soList = new ArrayList<>();

        // Tách số trong chuỗi và thêm vào danh sách soList
        String temp = "";
        for (char c : inputString.toCharArray()) {
            if (Character.isDigit(c)) {
                temp += c;
            } else if (!temp.isEmpty()) {
                soList.add(Integer.parseInt(temp));
                temp = "";
            }
        }
        if (!temp.isEmpty()) {
            soList.add(Integer.parseInt(temp));
        }

        System.out.println("Chuỗi nhập ngẫu nhiên: " + inputString);
        System.out.println("Danh sách số: " + soList);
    }

    // Tính tổng tất cả các số trong danh sách soList
    public int tinhTongSo() {
        int tong = 0;
        for (int so : soList) {
            tong += so;
        }
        return tong;
    }

    // Tính tổng các số lẻ trong danh sách soList
    public int tinhTongSoLe() {
        int tongLe = 0;
        for (int so : soList) {
            if (so % 2 != 0) {
                tongLe += so;
            }
        }
        return tongLe;
    }

    // Tính tổng các số chẵn trong danh sách soList
    public int tinhTongSoChan() {
        int tongChan = 0;
        for (int so : soList) {
            if (so % 2 == 0) {
                tongChan += so;
            }
        }
        return tongChan;
    }

    // Cộng các chữ số trong danh sách soList
    public int congCacChuSo() {
        int tongChuSo = 0;
        for (int so : soList) {
            while (so > 0) {
                tongChuSo += so % 10;
                so /= 10;
            }
        }
        return tongChuSo; // Thêm dòng này để trả về tổng các chữ số
    }
}

public class Con extends Cha {

    // Phương thức tách chuỗi không lấy số (chỉ lấy các ký tự chữ)
    public String tachChuoiKhongLaySo() {
        StringBuilder chuoiKhongSo = new StringBuilder();
        for (char c : inputString.toCharArray()) {
            if (!Character.isDigit(c)) {
                chuoiKhongSo.append(c);
            }
        }
        return chuoiKhongSo.toString();
    }

    // Phương thức loại bỏ các giá trị trùng lặp trong danh sách soList
    public void loaiBoTrungLap() {
        Set<Integer> uniqueSet = new HashSet<>(soList);
        soList.clear();
        soList.addAll(uniqueSet);
    }

    // Phương thức đếm khoảng trắng trong chuỗi inputString
    public int demKhoangTrang() {
        int count = 0;
        for (char c : inputString.toCharArray()) {
            if (Character.isWhitespace(c)) {
                count++;
            }
        }
        return count;
    }

    // Phương thức cộng các số trong danh sách soList
    public int congTatCaSo() {
        return tinhTongSo(); // Sử dụng phương thức từ lớp Cha
    }

    // Phương thức hiển thị các số chia hết cho 5 trong danh sách soList
    public void hienThiSoChiaHetCho5() {
        System.out.print("Các số chia hết cho 5: ");
        for (int so : soList) {
            if (so % 5 == 0) {
                System.out.print(so + " ");
            }
        }
        System.out.println();
    }
}


<!---
KanzCT/KanzCT is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
