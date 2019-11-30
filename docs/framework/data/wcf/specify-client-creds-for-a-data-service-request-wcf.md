---
title: 'Instrukcje: Określanie poświadczeń klienta dla żądania usługi danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: bb6447c39c3de9605f6f7bc280da2778be2b3070
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568856"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Instrukcje: Określanie poświadczeń klienta dla żądania usługi danych (Usługi danych programu WCF)
Domyślnie Biblioteka klienta nie dostarcza poświadczeń podczas wysyłania żądania do usługi OData. Można jednak określić, że poświadczenia mają być wysyłane w celu uwierzytelniania żądań do usługi danych przez dostarczenie <xref:System.Net.NetworkCredential> właściwości <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md). W przykładzie w tym temacie pokazano, jak jawnie podać poświadczenia, które są używane przez klienta Usługi danych programu WCF podczas żądania danych z usługi danych.  
  
 W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md). Możesz również użyć [przykładowej usługi danych Northwind](https://go.microsoft.com/fwlink/?LinkId=187426) opublikowanej w witrynie sieci Web OData. Ta przykładowa usługa danych jest tylko do odczytu i próba zapisu spowoduje zwrócenie błędu. Przykładowe usługi danych w witrynie sieci Web OData umożliwiają uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony powiązanej z kodem dla pliku Extensible Application Markup Language (XAML), który jest stroną główną aplikacji Windows Presentation Framework. Ten przykład wyświetla wystąpienie `LoginWindow` do zbierania poświadczeń uwierzytelniania od użytkownika, a następnie używa tych poświadczeń podczas wykonywania żądania do usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje stronę główną aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony powiązanej z kodem dla okna, które jest używane do zbierania poświadczeń uwierzytelniania od użytkownika przed wysłaniem żądania do usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje nazwę logowania aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia programu .NET Framework  
 Następujące zagadnienia dotyczące zabezpieczeń mają zastosowanie do przykładu w tym temacie:  
  
- Aby sprawdzić, czy poświadczenia podane w tej przykładowej pracy, usługa danych Northwind musi używać schematu uwierzytelniania innego niż dostęp anonimowy. W przeciwnym razie witryna sieci Web hostującym usługę danych nie będzie żądać poświadczeń.  
  
- Poświadczenia użytkownika powinny być wymagane tylko podczas wykonywania i nie powinny być buforowane. Poświadczenia muszą być zawsze przechowywane bezpiecznie.  
  
- Dane wysyłane z uwierzytelnianiem podstawowym i szyfrowanym nie są szyfrowane, więc dane mogą być widoczne przez atakującej. Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane zwykłym tekstem i mogą być przechwytywane.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczanie usługi danych programu WCF](securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług danych WCF](securing-wcf-data-services.md)
- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
