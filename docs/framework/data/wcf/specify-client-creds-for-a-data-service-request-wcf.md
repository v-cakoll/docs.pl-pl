---
title: "Porady: Określanie poświadczeń klienta dla żądania obsługi danych (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing requests
ms.assetid: 1632f9af-e45f-4363-9222-03823daa8e28
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09575a5f4790bc481b817412df2017e53ee18268
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-client-credentials-for-a-data-service-request-wcf-data-services"></a>Porady: Określanie poświadczeń klienta dla żądania obsługi danych (usługi danych WCF)
Domyślnie biblioteka klienta nie dostarcza poświadczenia podczas wysyłania żądania do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi. Jednak można określić, że poświadczenia wysyłane do uwierzytelniania żądań do usługi data podając <xref:System.Net.NetworkCredential> dla <xref:System.Data.Services.Client.DataServiceContext.Credentials%2A> właściwość <xref:System.Data.Services.Client.DataServiceContext>. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md). Przykład, w tym temacie przedstawiono sposób jawnie Podaj poświadczenia, które są używane przez [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klienta podczas żądania danych z usługi danych.  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Można również użyć [Northwind przykładowych danych usługi](http://go.microsoft.com/fwlink/?LinkId=187426) który jest opublikowany w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web; te przykładowe dane usługi jest tylko do odczytu i zwraca błąd, próba zapisania zmian. Przykładowe dane usługi na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web umożliwia uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony CodeBehind dla pliku Extensible Application Markup Language (XAML), który jest strona główna aplikacji Windows Presentation Framework. W tym przykładzie wyświetlono `LoginWindow` wystąpienia zbierać uwierzytelniania poświadczeń użytkownika, a następnie używa tych poświadczeń w żądaniu skierowanym do usługi data.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml.cs#clientcredentials)]  
 [!code-vb[Astoria Northwind Client#ClientCredentials](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentials.xaml.vb#clientcredentials)]
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje strony głównej aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentials.xaml#clientcredentialsxaml)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pochodzi ze strony CodeBehind dla okna, który służy do zbierania poświadczeń uwierzytelniania użytkownika przed wysłaniem żądania do usługi danych.  
  
 [!code-csharp[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml.cs#clientcredentialslogin)]  
 [!code-vb[Astoria Northwind Client#ClientCredentialsLogin](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/clientcredentialslogin.xaml.vb#clientcredentialslogin)]
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje nazwy logowania w aplikacji WPF.  
  
 [!code-xaml[Astoria Northwind Client#ClientCredentialsLoginXaml](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/clientcredentialslogin.xaml#clientcredentialsloginxaml)]  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Następujące zagadnienia dotyczące zabezpieczeń dotyczą na przykład w tym temacie:  
  
-   Aby sprawdzić, czy poświadczenia podane w tym przykładzie działają, Usługa danych Northwind musi używać schematu uwierzytelniania inne niż dostęp anonimowy. W przeciwnym razie usług danych hosta witryny sieci Web nie będą wymagane poświadczenia.  
  
-   Poświadczenia użytkownika powinno się żądać tylko podczas wykonywania i nie powinno być buforowane. Poświadczenia muszą zawsze być bezpiecznie przechowywane.  
  
-   Wysyłane podstawowe i uwierzytelnianie szyfrowane dane nie są szyfrowane, więc dane są widoczne dla atakujący dokonuje. Ponadto podstawowe poświadczenia uwierzytelniania (nazwa użytkownika i hasło) są wysyłane w zwykłym tekstem i może zostać przechwycona.  
  
 Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
