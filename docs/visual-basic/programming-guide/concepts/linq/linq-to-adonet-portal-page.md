---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 8c90783b56d6393ce3ac71945ed8ebffc8005ee1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84369183"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
LINQ to ADO.NET umożliwia wykonywanie zapytań dotyczących dowolnego wyliczalnego obiektu w ADO.NET przy użyciu modelu programowania programu Query-Integrated Language (LINQ).  
  
> [!NOTE]
> Dokumentacja LINQ to ADO.NET znajduje się w sekcji ADO.NET zestawu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Istnieją trzy oddzielne technologie ADO.NET Language-Integrated Query (LINQ): LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] i LINQ to Entities. LINQ to DataSet zapewnia bogatsze i zoptymalizowane zapytania dotyczące programu <xref:System.Data.DataSet> , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umożliwia bezpośrednie wykonywanie zapytań do SQL Server schematów bazy danych, a LINQ to Entities umożliwia wykonywanie zapytań do Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet>Jest jednym z najczęściej używanych składników w programie ADO.NET i jest elementem kluczowym modelu programowania rozłączonego, który ADO.NET jest zbudowany. Mimo tego wyeksponowanie <xref:System.Data.DataSet> ma jednak ograniczone możliwości zapytań.  
  
 LINQ to DataSet umożliwia tworzenie bogatszych możliwości zapytań w <xref:System.Data.DataSet> programie za pomocą tej samej funkcji zapytania, która jest dostępna dla wielu innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zapewnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty. W programie [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Po uruchomieniu aplikacji program [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy zapytania zintegrowane z językiem w modelu obiektów na SQL i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, program [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je z powrotem na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]obejmuje obsługę procedur składowanych i funkcji zdefiniowanych przez użytkownika w bazie danych oraz dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą Entity Data Model dane relacyjne są ujawniane jako obiekty w środowisku .NET. Sprawia to, że obiekt jest idealnym miejscem docelowym dla obsługi LINQ, dzięki czemu deweloperzy mogą tworzyć zapytania względem bazy danych w języku używanym do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ to Entities. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Zobacz też

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](index.md)
