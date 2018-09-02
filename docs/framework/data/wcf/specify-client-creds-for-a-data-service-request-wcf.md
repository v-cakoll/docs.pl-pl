---
title: 'Porady: Określanie poświadczeń klienta dla żądania usługi danych (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
ms.openlocfilehash: d0fbf01de05a02c03782af9e392a79b6dd3e8bee
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402524"
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Porady: Określanie poświadczeń klienta dla żądania usługi danych (WCF Data Services)
Domyślnie biblioteka klienta nie podaje poświadczeń, wysyłając żądanie do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Jednak można określić, że poświadczenia wysyłane do uwierzytelniania żądań do usługi danych przez przesłanie <xref:System.Net.NetworkCredential> dla <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). W przykładzie w tym temacie przedstawiono sposób jawnie podać poświadczenia, które są używane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta podczas żądania danych z usługi danych.  
  
 W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Można również użyć [Northwind przykładowe dane usługi](https://go.microsoft.com/fwlink/?LinkId=187426) opublikowaną w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web; te przykładowe dane usługi jest tylko do odczytu, a następnie próby zapisania zmiany zwraca błąd. Przykładowe dane usługi w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web umożliwia uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi z osobna strona kodu dla pliku Extensible Application Markup Language (XAML), który jest główna strona aplikacji Windows Presentation Framework. Ten przykład wyświetla `LoginWindow` wystąpienia, aby zbierać uwierzytelniania poświadczeń użytkownika, a następnie używa tych poświadczeń, gdy kieruje żądanie do usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje strony głównej aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi z osobna strona kodu dla okna, który służy do zbierania poświadczeń uwierzytelniania od użytkownika przed wysłaniem żądania do usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje nazwy logowania w aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Następujące zagadnienia dotyczące zabezpieczeń dotyczą na przykład w tym temacie:  
  
-   Aby sprawdzić, czy działają poświadczenia podane w tym przykładzie, Usługa danych Northwind musi używać schematu uwierzytelniania innego niż dostęp anonimowy. W przeciwnym razie witryna sieci Web usługi danych nie będzie żądać poświadczeń.  
  
-   Poświadczenia użytkownika powinno się żądać tylko wtedy podczas wykonywania i nie powinny być buforowane. Zawsze muszą być bezpiecznie przechowywane poświadczenia.  
  
-   Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, dzięki czemu dane są widoczne przez osobę atakującą. Ponadto poświadczenia uwierzytelniania podstawowego (nazwa użytkownika i hasło) są wysyłane jako zwykły tekst i mogą zostać przechwycone.  
  
 Aby uzyskać więcej informacji, zobacz [zabezpieczania usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
