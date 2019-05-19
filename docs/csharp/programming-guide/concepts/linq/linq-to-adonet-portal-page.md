---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 250b80d0c0b6d929fafbe20fc0555827e0f493f3
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881070"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Umożliwia wykonywanie zapytań za pośrednictwem dowolnego obiektu wyliczalny w ADO.NET przy użyciu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] model programowania.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Dokumentacja znajduje się w sekcji ADO.NET programu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Istnieją trzy osobne ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologii: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], i [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] zapewnia bardziej zaawansowane, zoptymalizowane zapytań <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pozwala na bezpośrednie wyszukiwanie schematy bazy danych programu SQL Server, a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] umożliwia zapytania [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest jednym z najczęściej używane składniki w ADO.NET i jest kluczowym elementem rozłączonych z ADO.NET jest oparta na modelu programowania. Mimo to dostępność, jednak <xref:System.Data.DataSet> ma ograniczone możliwości zapytania.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] Umożliwia tworzenie bogatszych możliwości kwerend <xref:System.Data.DataSet> przy użyciu tych samych funkcji kwerendy, które jest dostępne dla innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapewnia infrastrukturę czasu wykonywania dla zarządzania relacyjnymi bazami danych jako obiektami. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], model danych relacyjnej bazy danych jest zamapowana na model obiektów wyrażony w języku programowania dewelopera. Podczas wykonywania aplikacji, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy języku zintegrowanym zapytania w modelu obiektów programu SQL, a następnie wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je ponownie na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obejmuje obsługę procedur przechowywanych i funkcji zdefiniowanych przez użytkownika w bazie danych i dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], w relacyjnej bazie danych jest przedstawiany jako obiekty w środowisku .NET. To sprawia, że obiekt warstwy obiektu docelowego idealne rozwiązanie dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocy technicznej, co pozwoli deweloperom na formułowanie zapytania względem bazy danych z języka używany do tworzenia logiki biznesowej. Ta możliwość jest znana jako [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Zobacz [składnik LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
