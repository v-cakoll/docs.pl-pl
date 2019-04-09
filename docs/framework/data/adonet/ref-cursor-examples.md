---
title: Przykłady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dfad86c6d5c99d7a1b99d7cfbde165d5ec39f5f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158941"
---
# <a name="ref-cursor-examples"></a>Przykłady REF CURSOR
Przykłady REF CURSOR składają się z następujące trzy przykłady języka Visual Basic, które przedstawiają, za pomocą kursora REF CURSOR.  
  
|Przykład|Opis|  
|------------|-----------------|  
|[Parametry kursora REF CURSOR w OracleDataReader](../../../../docs/framework/data/adonet/ref-cursor-parameters-in-an-oracledatareader.md)|W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca parametr REF CURSOR i odczytuje wartość jako <xref:System.Data.OracleClient.OracleDataReader>.|  
|[Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader](../../../../docs/framework/data/adonet/retrieving-data-from-multiple-ref-cursors.md)|W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca dwa parametry REF CURSOR, a następnie odczytuje wartości za pomocą **Element OracleDataReader**.|  
|[Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR](../../../../docs/framework/data/adonet/filling-a-dataset-using-one-or-more-ref-cursors.md)|W tym przykładzie wykonuje procedury przechowywane PL/SQL, która zwraca dwa parametry REF CURSOR i wypełnia <xref:System.Data.DataSet> wierszy, które są zwracane.|  
  
 Aby korzystać z tych przykładów, może być konieczne utworzenie tabel bazy danych Oracle i należy utworzyć pakiet PL/SQL i treść pakietu.  
  
## <a name="creating-the-oracle-tables"></a>Tworzenie tabel Oracle  
 Te przykłady korzystanie z tabel, które są zdefiniowane w schemacie Oracle Scott/Tiger. Schemat bazy danych Oracle Scott/Tiger jest dołączana do większości instalacji programu Oracle. Jeśli w tym schemacie nie istnieje, możesz użyć pliku poleceń SQL w {OracleHome}\rdbms\admin\scott.sql tworzyć tabele i indeksy używane przez te przykłady.  
  
## <a name="creating-the-oracle-package-and-package-body"></a>Tworzenie pakietu programu Oracle i ciało pakietu  
 Te przykłady wymagają następujących pakietów PL/SQL i treść pakietu na serwerze. Utwórz następujący pakiet oprogramowania Oracle na serwerze bazy danych Oracle.  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS   
    TYPE T_CURSOR IS REF CURSOR;   
    PROCEDURE OPEN_ONE_CURSOR (N_EMPNO IN NUMBER,   
                               IO_CURSOR IN OUT T_CURSOR);   
    PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,   
                                DEPTCURSOR OUT T_CURSOR);  
END CURSPKG;  
/   
```  
  
 Utwórz następujące ciało pakietu oprogramowania Oracle na serwerze bazy danych Oracle.  
  
```sql
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
  
## <a name="see-also"></a>Zobacz także

- [Oracle REF CURSOR](../../../../docs/framework/data/adonet/oracle-ref-cursors.md)
- [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
