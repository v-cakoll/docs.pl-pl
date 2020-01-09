---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635551"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
LINQ to ADO.NET umożliwia wykonywanie zapytań dotyczących dowolnego wyliczalnego obiektu w ADO.NET przy użyciu modelu programowania programu Query-Integrated Language (LINQ).  
  
> [!NOTE]
> Dokumentacja LINQ to ADO.NET znajduje się w sekcji ADO.NET zestawu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Istnieją trzy oddzielne technologie ADO.NET Language-Integrated Query (LINQ): LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ to DataSet zapewnia bogatsze i zoptymalizowane zapytania dotyczące <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umożliwia bezpośrednie wysyłanie zapytań do SQL Server schematów bazy danych, a LINQ to Entities umożliwia wykonywanie zapytań do Entity Data Model.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> jest jednym z najczęściej używanych składników w ADO.NET, a to kluczowy element w odłączonym modelu programowania, który ADO.NET jest oparty. Mimo tego wyeksponowanie <xref:System.Data.DataSet> ma ograniczone możliwości zapytań.  
  
 LINQ to DataSet umożliwia tworzenie bogatszych możliwości zapytań do <xref:System.Data.DataSet> za pomocą tej samej funkcji zapytania, która jest dostępna dla wielu innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] udostępnia infrastrukturę czasu wykonywania do zarządzania danymi relacyjnymi jako obiekty. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]model danych relacyjnej bazy danych jest mapowany na model obiektów wyrażony w języku programowania dewelopera. Podczas wykonywania aplikacji [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy zapytania zintegrowane z językiem w modelu obiektów na SQL i wysyła je do bazy danych w celu wykonania. Gdy baza danych zwróci wyniki, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] przetłumaczy je z powrotem na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obejmuje obsługę procedur składowanych i funkcji zdefiniowanych przez użytkownika w bazie danych oraz dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 Za pomocą Entity Data Model dane relacyjne są ujawniane jako obiekty w środowisku .NET. Sprawia to, że obiekt jest idealnym miejscem docelowym dla obsługi LINQ, dzięki czemu deweloperzy mogą tworzyć zapytania względem bazy danych w języku używanym do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ to Entities. Aby uzyskać więcej informacji, zobacz [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) .  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie zintegrowane z językiem (LINQ)C#()](./index.md)
