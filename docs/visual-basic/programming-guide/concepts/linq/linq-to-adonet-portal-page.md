---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 25ec71086d501e6ac9be22871563b0fb4e3cfb8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957582"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
LINQ to ADO.NET umożliwia wykonywanie zapytań dotyczących dowolnego wyliczalnego obiektu w ADO.NET przy użyciu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] modelu programowania.  
  
> [!NOTE]
> Dokumentacja LINQ to ADO.NET znajduje się w sekcji ADO.NET zestawu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Istnieją trzy oddzielne technologie ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] : LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ to DataSet zapewnia bogatsze i zoptymalizowane zapytania dotyczące programu <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umożliwia bezpośrednie wykonywanie zapytań do SQL Server schematów bazy danych, a LINQ to Entities umożliwia wykonywanie zapytań do Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest jednym z najczęściej używanych składników w programie ADO.NET i jest elementem kluczowym modelu programowania rozłączonego, który ADO.NET jest zbudowany. Mimo tego wyeksponowanie <xref:System.Data.DataSet> ma jednak ograniczone możliwości zapytań.  
  
 LINQ to DataSet umożliwia tworzenie bogatszych możliwości zapytań w <xref:System.Data.DataSet> programie za pomocą tej samej funkcji zapytania, która jest dostępna dla wielu innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zapewnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]programie model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Po uruchomieniu aplikacji program [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy zapytania zintegrowane z językiem w modelu obiektów na SQL i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, program [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je z powrotem na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]obejmuje obsługę procedur składowanych i funkcji zdefiniowanych przez użytkownika w bazie danych oraz dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą Entity Data Model dane relacyjne są ujawniane jako obiekty w środowisku .NET. Sprawia to, że obiekt jest idealnym celem [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obsługi, dzięki czemu deweloperzy mogą tworzyć zapytania względem bazy danych w języku używanym do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ to Entities. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie zintegrowane z językiem (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
