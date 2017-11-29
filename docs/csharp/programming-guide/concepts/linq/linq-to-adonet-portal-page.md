---
title: LINQ to ADO.NET (Portal Page)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 649497f28ef5f9758ba6d6df13a91a1246d12136
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Portal Page)
[!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)]Umożliwia zapytanie dotyczące dowolny obiekt wyliczalny w [!INCLUDE[vstecado](~/includes/vstecado-md.md)] przy użyciu [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] model programowania.  
  
> [!NOTE]
>  [!INCLUDE[linq_adonet](~/includes/linq-adonet-md.md)] Dokumentacji znajduje się w sekcji ADO.NET programu .NET Framework SDK: [LINQ i ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec).  
  
 Istnieją trzy oddzielne ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] technologii: [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)], [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], i [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]zapewnia bogaty i zoptymalizowane obsługę zapytań <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] umożliwia bezpośrednio odpytywać [!INCLUDE[ssNoVersion](~/includes/ssnoversion-md.md)] bazy danych, schematów, i [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)] umożliwia zapytania [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)].  
  
## <a name="linq-to-dataset"></a>LINQ do DataSet  
 <xref:System.Data.DataSet> Jest jednym z najpopularniejszych składniki [!INCLUDE[vstecado](~/includes/vstecado-md.md)], i jest kluczowym elementem odłączonego programowania modelu [!INCLUDE[vstecado](~/includes/vstecado-md.md)] jest wbudowany w program. Mimo to dostępność, jednak <xref:System.Data.DataSet> ma ograniczone możliwości zapytania.  
  
 [!INCLUDE[linq_dataset](~/includes/linq-dataset-md.md)]Umożliwia tworzenie bardziej rozbudowane możliwości zapytania <xref:System.Data.DataSet> przy użyciu zapytania funkcji dostępnego dla innych źródeł danych.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ do SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]zapewnia infrastrukturę środowiska wykonawczego do zarządzania jako obiekty relacyjnej bazie danych. W [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], modelu danych relacyjnej bazy danych jest mapowany na model obiektowy wyrażone w języku programowania dewelopera. Podczas wykonywania aplikacji, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy zapytania o języku zintegrowanym w modelu obiektów na SQL i wysyła je do bazy danych do wykonania. Gdy baza danych zwraca wyniki, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] tłumaczy je do obiektów, które można manipulować.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]obsługuje procedury składowane i funkcje zdefiniowane przez użytkownika w bazie danych i dziedziczenie w modelu obiektów.  
  
 Aby uzyskać więcej informacji, zobacz [LINQ do SQL](https://msdn.microsoft.com/library/bb386976).  
  
## <a name="linq-to-entities"></a>LINQ do Jednostek  
 Za pomocą [!INCLUDE[adonet_edm](~/includes/adonet-edm-md.md)], relacyjnej bazie danych jest ujawniona jako obiekty w środowisku .NET. Dzięki temu warstwy obiektu docelowego nadaje się doskonale dla obiekt [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] pomocy technicznej, co umożliwia deweloperom do formułowania zapytań dotyczących bazy danych z język używany do tworzenia logiki biznesowej. Ta funkcja jest nazywany [!INCLUDE[linq_entities](~/includes/linq-entities-md.md)]. Zobacz [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ i ADO.NET](http://msdn.microsoft.com/library/bf0c8f93-3ff7-49f3-8aed-f2b7ac938dec)  
 [Zapytanie o języku zintegrowanym (LINQ) (C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
