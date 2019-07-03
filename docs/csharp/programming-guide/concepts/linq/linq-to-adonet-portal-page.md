---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 8c39582ee95619bfddc7b89380e0a86305eeac27
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539515"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
LINQ to ADO.NET umożliwia wykonywanie zapytań za pośrednictwem dowolnego obiektu wyliczalny w ADO.NET przy użyciu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] model programowania.  
  
> [!NOTE]
>  LINQ to ADO.NET dokumentacji znajduje się w sekcji ADO.NET programu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 Istnieją trzy osobne ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologii: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]i LINQ to Entities. LINQ do DataSet zawiera bardziej zaawansowane, zoptymalizowane zapytań <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pozwala na bezpośrednie wyszukiwanie schematy bazy danych programu SQL Server i składniku LINQ to Entities umożliwia zapytania modelu danych jednostki.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest jednym z najczęściej używane składniki w ADO.NET i jest kluczowym elementem rozłączonych z ADO.NET jest oparta na modelu programowania. Mimo to dostępność, jednak <xref:System.Data.DataSet> ma ograniczone możliwości zapytania.  
  
 LINQ do zestawu danych umożliwia tworzenie bogatszych możliwości kwerend <xref:System.Data.DataSet> przy użyciu tych samych funkcji kwerendy, które jest dostępne dla innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapewnia infrastrukturę czasu wykonywania dla zarządzania relacyjnymi bazami danych jako obiektami. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], model danych relacyjnej bazy danych jest zamapowana na model obiektów wyrażony w języku programowania dewelopera. Podczas wykonywania aplikacji, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy języku zintegrowanym zapytania w modelu obiektów programu SQL, a następnie wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je ponownie na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obejmuje obsługę procedur przechowywanych i funkcji zdefiniowanych przez użytkownika w bazie danych i dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą modelu Entity Data Model w relacyjnej bazie danych jest udostępniany jako obiekty w środowisku .NET. To sprawia, że obiekt warstwy obiektu docelowego idealne rozwiązanie dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocy technicznej, co pozwoli deweloperom na formułowanie zapytania względem bazy danych z języka używany do tworzenia logiki biznesowej. Ta możliwość jest znana jako LINQ to Entities. Zobacz [składnik LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
