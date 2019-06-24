---
title: LINQ to ADO.NET (Portal Page)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 21d6ddb4b793d2502b315888d79fb826741fed2e
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307484"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Umożliwia wykonywanie zapytań za pośrednictwem dowolnego obiektu wyliczalny w ADO.NET przy użyciu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] model programowania.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Dokumentacja znajduje się w sekcji ADO.NET programu .NET Framework SDK: [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Istnieją trzy osobne ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologii: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], i [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] zapewnia bardziej zaawansowane, zoptymalizowane zapytań <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] pozwala na bezpośrednie wyszukiwanie schematy bazy danych programu SQL Server, a [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] umożliwia zapytania modelu danych jednostki.  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest jednym z najczęściej używane składniki w ADO.NET i jest kluczowym elementem rozłączonych z ADO.NET jest oparta na modelu programowania. Mimo to dostępność, jednak <xref:System.Data.DataSet> ma ograniczone możliwości zapytania.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)] Umożliwia tworzenie bogatszych możliwości kwerend <xref:System.Data.DataSet> przy użyciu tych samych funkcji kwerendy, które jest dostępne dla innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] zapewnia infrastrukturę czasu wykonywania dla zarządzania relacyjnymi bazami danych jako obiektami. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], model danych relacyjnej bazy danych jest zamapowana na model obiektów wyrażony w języku programowania dewelopera. Podczas wykonywania aplikacji, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy języku zintegrowanym zapytania w modelu obiektów programu SQL, a następnie wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je ponownie na obiekty, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] obejmuje obsługę procedur przechowywanych i funkcji zdefiniowanych przez użytkownika w bazie danych i dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą modelu Entity Data Model w relacyjnej bazie danych jest udostępniany jako obiekty w środowisku .NET. To sprawia, że obiekt warstwy obiektu docelowego idealne rozwiązanie dla [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocy technicznej, co pozwoli deweloperom na formułowanie zapytania względem bazy danych z języka używany do tworzenia logiki biznesowej. Ta możliwość jest znana jako [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Zobacz [składnik LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz także

- [LINQ i ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Zapytanie o języku zintegrowanym (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
