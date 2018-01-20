---
title: "Porady: kwerenda zwraca typów złożonych"
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
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: cae0cc50b18641634fc8109fb29eeb30e9cf7cd8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a>Porady: kwerenda zwraca typów złożonych
W tym temacie przedstawiono sposób wykonania [!INCLUDE[esql](../../../../../includes/esql-md.md)] kwerendę, która zwraca jednostki typu obiektów, które zawierają właściwość typu złożonego.  
  
### <a name="to-run-the-code-in-this-example"></a>Aby uruchomić kod w tym przykładzie  
  
1.  Dodaj [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu i konfigurowanie projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
2.  Na stronie kodu aplikacji, Dodaj następujący `using` instrukcje (`Imports` w języku Visual Basic):  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  Kliknij dwukrotnie plik edmx do wyświetlenia w modelu [okna przeglądarki modelu](http://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) programu Entity Designer. Na powierzchni Projektanta obiektów wybierz `Email` i `Phone` właściwości `Contact` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz **Refaktoryzuj na nowy typ złożony**.  
  
4.  Nowy typ złożony z wybranym `Email` i `Phone` właściwości jest dodawane do **przeglądarki modelu**. Typ złożony podano nazwę domyślną: Zmień nazwę typu do `EmailPhone` w **właściwości** okna. Ponadto nowy `ComplexProperty` właściwość została dodana do `Contact` typu jednostki. Zmień nazwę właściwości`EmailPhoneComplexType.`  
  
     Uzyskać informacji o tworzeniu i modyfikowaniu typów złożonych za pomocą Kreatora modelu danych jednostki, zobacz [porady: Refaktoryzuj istniejącej właściwości w złożonych właściwości typu](http://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) i [jak: utworzyć i zmodyfikować typów złożonych](http://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wykonuje zapytanie zwraca kolekcję `Contact` obiekty i wyświetla dwie właściwości `Contact` obiektów: `ContactID` i wartości `EmailPhoneComplexType` typu złożonego.  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
