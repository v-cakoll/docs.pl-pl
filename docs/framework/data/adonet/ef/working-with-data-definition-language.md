---
title: Praca z językiem definicji danych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
ms.openlocfilehash: 83d6fc1294f6aa37389db9e517b02866ef000b50
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854227"
---
# <a name="working-with-data-definition-language"></a>Praca z językiem definicji danych
Począwszy od .NET Framework w wersji 4 Entity Framework obsługuje język definicji danych (DDL). Pozwala to na tworzenie lub usuwanie wystąpienia bazy danych na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).  
  
 Poniższe metody dotyczące <xref:System.Data.Objects.ObjectContext> używania parametrów połączenia i zawartości SSDL do wykonania następujących czynności: Utwórz lub Usuń bazę danych, sprawdź, czy baza danych istnieje, i Wyświetl wygenerowany skrypt DDL:  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
- <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
- <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
> Wykonywanie poleceń języka DDL przyjmuje odpowiednie uprawnienia.  
  
 Wymienione wcześniej metody delegowania większość pracy do podstawowego dostawcy danych ADO.NET. Jest on odpowiedzialny za zapewnienie, że Konwencja nazewnictwa używana do generowania obiektów bazy danych jest spójna z konwencjami używanymi do wykonywania zapytań i aktualizacji.  
  
 Poniższy przykład pokazuje, jak wygenerować bazę danych na podstawie istniejącego modelu. Dodaje również nowy obiekt Entity do kontekstu obiektu, a następnie zapisuje go w bazie danych.  
  
## <a name="procedures"></a>Procedury  
  
### <a name="to-define-a-database-based-on-the-existing-model"></a>Aby zdefiniować bazę danych opartą na istniejącym modelu  
  
1. Utwórz aplikację konsolową.  
  
2. Dodaj istniejący model do aplikacji.  
  
    1. Dodaj pusty model o nazwie `SchoolModel`. Aby utworzyć pusty model, zobacz [How to: Utwórz nowy temat pliku](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716703(v=vs.100)) . edmx.  
  
     Plik SchoolModel. edmx zostanie dodany do projektu.  
  
    1. Skopiuj zawartość koncepcyjną, magazynową i mapowanie dla modelu szkoły z tematu [model szkoły](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) .  
  
    2. Otwórz plik SchoolModel. edmx i wklej zawartość w `edmx:Runtime` tagach.  
  
3. Dodaj następujący kod do funkcji main. Kod inicjuje parametry połączenia z serwerem bazy danych, przegląda Skrypt DDL, tworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
