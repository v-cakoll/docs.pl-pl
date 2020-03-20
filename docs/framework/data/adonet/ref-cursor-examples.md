---
title: Przykłady REF CURSOR
ms.date: 03/30/2017
ms.assetid: c257da03-c6c9-4cf8-b591-b7740a962c40
ms.openlocfilehash: dc82648ff5a565c9b4d6fa593433ee1e22249d93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149138"
---
# <a name="ref-cursor-examples"></a><span data-ttu-id="7d125-102">Przykłady REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7d125-102">REF CURSOR Examples</span></span>
<span data-ttu-id="7d125-103">Przykłady kursora REF składają się z następujących trzech przykładów programu Microsoft Visual Basic, które demonstrują przy użyciu cursorów REF.</span><span class="sxs-lookup"><span data-stu-id="7d125-103">The REF CURSOR examples are comprised of the following three Microsoft Visual Basic examples that demonstrate using REF CURSORs.</span></span>  
  
|<span data-ttu-id="7d125-104">Sample</span><span class="sxs-lookup"><span data-stu-id="7d125-104">Sample</span></span>|<span data-ttu-id="7d125-105">Opis</span><span class="sxs-lookup"><span data-stu-id="7d125-105">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7d125-106">Parametry kursora REF CURSOR w OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="7d125-106">REF CURSOR Parameters in an OracleDataReader</span></span>](ref-cursor-parameters-in-an-oracledatareader.md)|<span data-ttu-id="7d125-107">W tym przykładzie wykonuje procedurę składowaną PL/SQL, która zwraca parametr <xref:System.Data.OracleClient.OracleDataReader>REF CURSOR i odczytuje wartość jako .</span><span class="sxs-lookup"><span data-stu-id="7d125-107">This example executes a PL/SQL stored procedure that returns a REF CURSOR parameter, and reads the value as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>|  
|[<span data-ttu-id="7d125-108">Pobieranie danych z wielu kursorów REF CURSOR przy użyciu OracleDataReader</span><span class="sxs-lookup"><span data-stu-id="7d125-108">Retrieving Data from Multiple REF CURSORs Using an OracleDataReader</span></span>](retrieving-data-from-multiple-ref-cursors.md)|<span data-ttu-id="7d125-109">W tym przykładzie wykonuje procedurę składowaną PL/SQL, która zwraca dwa parametry KURSORA REF i odczytuje wartości za pomocą **czytnika OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="7d125-109">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and reads the values using an **OracleDataReader**.</span></span>|  
|[<span data-ttu-id="7d125-110">Wypełnianie zestawu danych przy użyciu przynajmniej jednego kursora REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7d125-110">Filling a DataSet Using One or More REF CURSORs</span></span>](filling-a-dataset-using-one-or-more-ref-cursors.md)|<span data-ttu-id="7d125-111">W tym przykładzie wykonuje pl/SQL procedura składowana, która zwraca <xref:System.Data.DataSet> dwa parametry KURSOR REF i wypełnia wiersze, które są zwracane.</span><span class="sxs-lookup"><span data-stu-id="7d125-111">This example executes a PL/SQL stored procedure that returns two REF CURSOR parameters, and fills a <xref:System.Data.DataSet> with the rows that are returned.</span></span>|  
  
 <span data-ttu-id="7d125-112">Aby użyć tych przykładów, może być konieczne utworzenie tabel Oracle i należy utworzyć pakiet PL/SQL i treść pakietu.</span><span class="sxs-lookup"><span data-stu-id="7d125-112">To use these examples, you may need to create the Oracle tables, and you must create a PL/SQL package and package body.</span></span>  
  
## <a name="creating-the-oracle-tables"></a><span data-ttu-id="7d125-113">Tworzenie tabel Oracle</span><span class="sxs-lookup"><span data-stu-id="7d125-113">Creating the Oracle Tables</span></span>  
 <span data-ttu-id="7d125-114">W tych przykładach użyto tabel zdefiniowanych w schemacie Oracle Scott/Tiger.</span><span class="sxs-lookup"><span data-stu-id="7d125-114">These examples use tables that are defined in the Oracle Scott/Tiger schema.</span></span> <span data-ttu-id="7d125-115">Schemat Oracle Scott/Tiger jest dołączony do większości instalacji Oracle.</span><span class="sxs-lookup"><span data-stu-id="7d125-115">The Oracle Scott/Tiger schema is included with most Oracle installations.</span></span> <span data-ttu-id="7d125-116">Jeśli ten schemat nie istnieje, można użyć pliku poleceń SQL w {OracleHome}\rdbms\admin\scott.sql, aby utworzyć tabele i indeksy używane przez te przykłady.</span><span class="sxs-lookup"><span data-stu-id="7d125-116">If this schema does not exist, you can use the SQL commands file in {OracleHome}\rdbms\admin\scott.sql to create the tables and indexes used by these examples.</span></span>  
  
## <a name="creating-the-oracle-package-and-package-body"></a><span data-ttu-id="7d125-117">Tworzenie pakietu Oracle i treści pakietów</span><span class="sxs-lookup"><span data-stu-id="7d125-117">Creating the Oracle Package and Package Body</span></span>  
 <span data-ttu-id="7d125-118">Te przykłady wymagają następującego pakietu PL/SQL i treści pakietu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="7d125-118">These examples require the following PL/SQL package and package body on your server.</span></span> <span data-ttu-id="7d125-119">Utwórz następujący pakiet Oracle na serwerze Oracle.</span><span class="sxs-lookup"><span data-stu-id="7d125-119">Create the following Oracle package on the Oracle server.</span></span>  
  
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
  
 <span data-ttu-id="7d125-120">Utwórz następującą treść pakietu Oracle na serwerze Oracle.</span><span class="sxs-lookup"><span data-stu-id="7d125-120">Create the following Oracle package body on the Oracle server.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d125-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d125-121">See also</span></span>

- [<span data-ttu-id="7d125-122">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="7d125-122">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)
- [<span data-ttu-id="7d125-123">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d125-123">ADO.NET Overview</span></span>](ado-net-overview.md)
