---
title: Przykłady kursora REF
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: 9593a30524b7d8161903b840e1bdb0ee007027a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353550"
---
# <a name="ref-cursor-examples"></a>Przykłady kursora REF
Przykłady REF CURSOR składają się następujące trzy przykładów programu Microsoft Visual Basic, które pokazanie sposobu używania kursory REF.  
  
|Przykład|Opis|  
|------------|-----------------|  
|[Parametry kursora REF CURSOR w OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|W tym przykładzie wykonuje procedury składowane PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|W tym przykładzie wykonuje procedury składowane PL/SQL, która zwraca dwa parametry REF CURSOR i odczytuje wartości przy użyciu **OracleDataReader**.|  
|[Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|W tym przykładzie wykonuje procedury składowane PL/SQL, która zwraca dwa parametry REF CURSOR i wpisuje <xref:System.Data.DataSet> z wierszy, które są zwracane.|  
  
 Aby użyć tych przykładów, może być konieczne utworzenie tabel Oracle i należy utworzyć pakiet PL/SQL i treść pakietu.  
  
## <a name="creating-the-oracle-tables"></a>Tworzenie tabel programu Oracle  
 Poniższe przykłady użycia tabel, które są zdefiniowane w schemacie Oracle Scott/Tiger. Schemat Oracle Scott/Tiger jest dołączana do większości instalacji programu Oracle. Jeśli ten schemat nie istnieje, możesz użyć pliku poleceń SQL w {OracleHome}\rdbms\admin\scott.sql do tworzenia tabel i indeksów używane przez te przykłady.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Tworzenie pakietu programu Oracle i treść pakietu  
 Poniższe przykłady wymagają następujący pakiet PL/SQL i treść pakietu na serwerze. Utwórz następujący pakiet programu Oracle na serwerze programu Oracle.  
  
```  
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 Utwórz następujące treść pakietu programu Oracle na serwerze programu Oracle.  
  
```  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS  
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,  
                               IO_CURSOR IN OUT T_CURSOR)  
    IS   
        V_CURSOR T_CURSOR;   
    BEGIN   
        IF N_EMPNO <> 0   
        THEN  
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO   
                  AND EMP.EMPNO = N_EMPNO;  
  
        ELSE   
             OPEN V_CURSOR FOR   
             SELECT EMP.EMPNO, EMP.ENAME, DEPT.DEPTNO, DEPT.DNAME   
                  FROM EMP, DEPT   
                  WHERE EMP.DEPTNO = DEPT.DEPTNO;  
  
        END IF;  
        IO_CURSOR := V_CURSOR;   
    END OPEN_ONE_CURSOR;   
  
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,  
                                DEPTCURSOR OUT T_CURSOR)  
    IS   
        V_CURSOR1 T_CURSOR;   
        V_CURSOR2 T_CURSOR;   
    BEGIN   
        OPEN V_CURSOR1 FOR SELECT * FROM EMP;  
        OPEN V_CURSOR2 FOR SELECT * FROM DEPT;  
        EMPCURSOR  := V_CURSOR1;   
        DEPTCURSOR := V_CURSOR2;   
    END OPEN_TWO_CURSORS;   
END CURSPKG;  
/  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
