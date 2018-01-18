---
title: "Praca z języka definicji danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ec50083d-44f4-4093-9b23-5eacd601f96e
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8b363105f0dd6978d4e59678fb7cd1b3f1d721df
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="working-with-data-definition-language"></a>Praca z języka definicji danych
Począwszy od [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] w wersji 4, [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] obsługuje języka definicji danych (DDL). Umożliwia to tworzenie lub usuwanie wystąpienia bazy danych, na podstawie parametrów połączenia i metadanych modelu magazynu (SSDL).  
  
 Następujących metod na <xref:System.Data.Objects.ObjectContext> Użyj parametrów połączenia i zawartość pliku SSDL, aby wykonać następujące czynności: Utwórz lub Usuń bazę danych, sprawdź, czy baza danych istnieje i wyświetlić wygenerowany skrypt DDL:  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DeleteDatabase%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.DatabaseExists%2A>  
  
-   <xref:System.Data.Objects.ObjectContext.CreateDatabaseScript%2A>  
  
> [!NOTE]
>  Wykonywanie polecenia języka DDL zakłada wystarczających uprawnień.  
  
 Metody wcześniej wymienione delegować większość pracy do podstawowego dostawcy danych ADO.NET. Jest dostawcy odpowiedzialność za upewnij się, że konwencji nazewnictwa służący do generowania obiektów bazy danych jest zgodne z konwencjami używane do wykonywania zapytań i aktualizacji.  
  
 Poniższy przykład przedstawia sposób generowania bazy danych na podstawie istniejącego modelu. On również dodaje nowy obiekt jednostki do kontekstu obiektów i jest zapisywany w bazie danych.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-define-a-database-based-on-the-existing-model"></a>Aby określić bazę danych na podstawie istniejącego modelu  
  
1.  Tworzenie aplikacji konsoli.  
  
2.  Dodawanie istniejącego modelu do aplikacji.  
  
    1.  Dodaj pusty model o nazwie `SchoolModel`. Aby utworzyć pusty model, zobacz [porady: Tworzenie nowego edmx pliku](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2) tematu.  
  
     Plik SchoolModel.edmx zostanie dodany do projektu.  
  
    1.  Kopiowanie pojęciach, magazynu i mapowanie zawartości dla modelu służbowe [modelu służbowe](http://msdn.microsoft.com/en-us/859a9587-81ea-4a45-9bc0-f8d330e1adac) tematu.  
  
    2.  Otwórz plik SchoolModel.edmx i Wklej zawartość w `edmx:Runtime` tagów.  
  
3.  Dodaj następujący kod do funkcji main. Kod inicjuje parametry połączenia z serwerem bazy danych, widoki skryptu DDL utworzy bazę danych, dodaje nową jednostkę do kontekstu i zapisuje zmiany w bazie danych.  
  
     [!code-csharp[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/csharp/VS_Snippets_Data/DP ObjectServices Concepts/CS/Source.cs#ddl)]
     [!code-vb[DP ObjectServices Concepts#DDL](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP ObjectServices Concepts/VB/Source.vb#ddl)]
