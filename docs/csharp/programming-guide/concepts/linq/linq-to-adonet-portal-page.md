---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 84412e43a9d6b1e256e4ac8306a94126a3eaaaf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635551"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
LINQ do ADO.NET umożliwia wykonywanie zapytań przez dowolny obiekt wyliczany w ADO.NET przy użyciu modelu programowania ZAPytanie zintegrowane z językiem (LINQ).  
  
> [!NOTE]
> Dokumentacja LINQ do ADO.NET znajduje się w sekcji ADO.NET sdk .NET Framework: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Istnieją trzy oddzielne technologie ADO.NET zapytań zintegrowanych z językiem (LINQ): LINQ do DataSet i [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]LINQ do jednostek. LINQ do Zestawu danych zapewnia bogatsze, <xref:System.Data.DataSet>zoptymalizowane zapytanie za pomocą , [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umożliwia bezpośrednie wykonywanie zapytań o szemaki bazy danych programu SQL Server, a LINQ do jednostek umożliwia wykonywanie zapytań o model danych jednostki.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 Jest <xref:System.Data.DataSet> to jeden z najczęściej używanych składników w ADO.NET i jest kluczowym elementem odłączonego modelu programowania, na który opiera się ADO.NET. Pomimo tego znaczenia, <xref:System.Data.DataSet> jednak ma ograniczone możliwości zapytania.  
  
 LINQ do DataSet umożliwia tworzenie bogatszych <xref:System.Data.DataSet> możliwości zapytania przy użyciu tej samej funkcji zapytania, która jest dostępna dla wielu innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zapewnia infrastrukturę w czasie wykonywania do zarządzania danymi relacyjnymi jako obiektami. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]programie model danych relacyjnej bazy danych jest mapowany na model obiektu wyrażony w języku programowania dewelopera. Podczas wykonywania aplikacji, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy język zintegrowanych zapytań w modelu obiektu do SQL i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] wyniki, tłumaczy je z powrotem na obiekty, którymi można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zawiera obsługę procedur przechowywanych i funkcji zdefiniowanych przez użytkownika w bazie danych oraz dziedziczenia w modelu obiektu.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pośrednictwem modelu danych jednostki dane relacyjne są udostępniane jako obiekty w środowisku .NET. To sprawia, że warstwa obiektu idealnym celem dla obsługi LINQ, dzięki czemu deweloperzy do formułowania kwerend y względem bazy danych z języka używanego do tworzenia logiki biznesowej. Ta funkcja jest znana jako LINQ do jednostek. Zobacz [LINQ do jednostek, aby](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie zintegrowane z językiem (LINQ) (C#)](./index.md)
