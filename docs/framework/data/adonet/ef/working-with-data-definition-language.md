---
title: Praca z językiem definicji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 25d7f49644996d87ddb5d191dc313916c0ca6fbb
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213981"
---
# <a name="working-with-data-definition-language"></a>Praca z językiem definicji danych
Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w wersji 4 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje języka definicji danych (DDL). Dzięki temu można utworzyć lub usunąć wystąpienie bazy danych na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).  
  
 Następujące metody w <xref:System.Data.Objects.ObjectContext> za pomocą parametrów połączenia i zawartości SSDL wykonywać następujące czynności: Tworzenie lub usuwanie bazy danych, sprawdź, czy baza danych istnieje i wyświetlić wygenerowany skrypt języka DDL:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Wykonywanie polecenia języka DDL zakłada wystarczających uprawnień.  
  
 Metody wymienione wcześniej delegować większość pracy do podstawowego dostawcy danych ADO.NET. Jest odpowiedzialny za dostawcy upewnij się, że Konwencja nazewnictwa służącego do generowania obiektów bazy danych zgodne z konwencjami, używane do tworzenia zapytań i aktualizacji.  
  
 Poniższy przykład pokazuje, jak wygenerować bazy danych na podstawie istniejącego modelu. On również dodaje nowy obiekt jednostki do kontekstu obiektów i zapisuje je w bazie danych.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Aby zdefiniować bazę danych na podstawie istniejącego modelu  
  
1.  Utwórz aplikację konsoli.  
  
2.  Dodawanie istniejącego modelu do aplikacji.  
  
    1.  Dodaj pusty modelu o nazwie `SchoolModel`. Aby utworzyć pusty model, zobacz [porady: Tworzenie nowego edmx pliku](https://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2) tematu.  
  
     Plik SchoolModel.edmx zostanie dodany do projektu.  
  
    1.  Skopiuj pojęciach, magazynu i mapowanie zawartości przez model do szkoły [modelu School](https://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) tematu.  
  
    2.  Otwórz plik SchoolModel.edmx i Wklej zawartość w ramach `edmx:Runtime` tagów.  
  
3.  Dodaj następujący kod do funkcji main. Ten kod inicjalizuje parametry połączenia z serwerem bazy danych, widoki, skrypt DDL tworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
