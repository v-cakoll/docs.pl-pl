---
title: "Porady: tworzenie aplikacji Framework prezentacji asynchroniczne systemu Windows (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 351812d632a394612e8ea241b7fea388066b4199
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Porady: tworzenie aplikacji Framework prezentacji asynchroniczne systemu Windows (usługi danych WCF)
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], można powiązać danych uzyskanych z usług danych do elementu interfejsu użytkownika aplikacji Windows Presentation Framework (WPF). Aby uzyskać więcej informacji, zobacz [wiązanie danych do kontrolek](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Możesz również wykonać operacje z usługą danych w sposób asynchroniczny, co umożliwia to aplikacji kontynuować odpowiadać podczas oczekiwania na odpowiedź na żądanie obsługi danych. Aplikacje dla programu Silverlight są wymagane do uzyskania dostępu do usługi danych asynchronicznie. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 W tym temacie przedstawiono sposób asynchronicznego dostępu do usługi danych i ich powiązania wyniki do elementów aplikacji WPF. Przykłady w tym temacie usługę Northwind przykładowych danych i dane klienta automatycznie wygenerowaną usługi klasy. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje okna aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Przykład  
 Następująca strona CodeBehind dla pliku XAML wykonuje asynchroniczne zapytania przy użyciu usługi danych i wiąże wyniki elementów w oknie WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
