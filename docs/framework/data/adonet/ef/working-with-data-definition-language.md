---
title: Praca z językiem definicji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 75a214ad1099bf48dcb2c2d3b36bf07dc0524f8d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769583"
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
  
1. Utwórz aplikację konsoli.  
  
2. Dodawanie istniejącego modelu do aplikacji.  
  
    1.  Dodaj pusty modelu o nazwie `SchoolModel`. Aby utworzyć pusty model, zobacz [jak: Tworzenie nowego edmx pliku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) tematu.  
  
     Plik SchoolModel.edmx zostanie dodany do projektu.  
  
    1.  Skopiuj pojęciach, magazynu i mapowanie zawartości przez model do szkoły [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) tematu.  
  
    2.  Otwórz plik SchoolModel.edmx i Wklej zawartość w ramach `edmx:Runtime` tagów.  
  
3. Dodaj następujący kod do funkcji main. Ten kod inicjalizuje parametry połączenia z serwerem bazy danych, widoki, skrypt DDL tworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
