---
title: 'Instrukcje: Tworzenie asynchronicznej aplikacji struktury prezentacji systemu Windows (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 820cb4aa39b49d63cf1acc31e6eb5aa56fd1ba03
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790993"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Instrukcje: Tworzenie asynchronicznej aplikacji struktury prezentacji systemu Windows (Usługi danych programu WCF)
Za [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pomocą programu można powiązać dane uzyskane z usługi danych z elementem interfejsu użytkownika aplikacji Windows Presentation Framework (WPF). Aby uzyskać więcej informacji, zobacz [Powiązywanie danych z kontrolkami](binding-data-to-controls-wcf-data-services.md). Można również wykonywać operacje na usłudze danych w sposób asynchroniczny, co umożliwia aplikacji dalsze reagowanie podczas oczekiwania na odpowiedź na żądanie usługi danych. Aplikacje dla programu Silverlight są wymagane do asynchronicznego uzyskiwania dostępu do usługi danych. Aby uzyskać więcej informacji, zobacz [operacje asynchroniczne](asynchronous-operations-wcf-data-services.md).  
  
 W tym temacie pokazano, jak w sposób asynchroniczny uzyskać dostęp do usługi danych i powiązać wyniki z elementami aplikacji WPF. Przykłady w tym temacie wykorzystują przykładową usługę danych Northwind i automatycznie wygenerowaną klasę usługi danych klienta. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje okno aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Przykład  
 Następująca Strona związana z kodem dla pliku XAML wykonuje asynchroniczne zapytanie przy użyciu usługi danych i wiąże wyniki do elementów w oknie WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
