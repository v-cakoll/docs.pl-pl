---
title: 'Porady: implementowanie logowania użytkownika przy użyciu usług aplikacji klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
ms.openlocfilehash: 1b1c5bebb5bd94f0a56dc6da303ef2503ab6dd4f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743813"
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Porady: implementowanie logowania użytkownika przy użyciu usług aplikacji klienta
Usługi aplikacji klienta można użyć do weryfikowania użytkowników za pomocą istniejącej [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi. Aby uzyskać informacje dotyczące sposobu konfigurowania [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi, zobacz [przy użyciu uwierzytelniania formularzy z Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Poniższe procedury zawierają opis do weryfikowania użytkowników za pośrednictwem usługi uwierzytelniania, gdy aplikacja jest skonfigurowana do korzystania z jednego z dostawców usługi uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usługi aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Zwykle będzie wykonywać wszystkie weryfikacji za pomocą `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody. Ta metoda zarządza interakcji z usługą uwierzytelniania za pośrednictwem dostawcy uwierzytelniania skonfigurowane. Aby uzyskać więcej informacji, zobacz [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Procedury uwierzytelniania formularzy wymagają dostępu do działającego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi uwierzytelniania. Wskazówki dotyczące testowania aplikacji klienckiej end-to-end usług funkcji, zobacz [wskazówki: Korzystanie z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>Dostawca poświadczeń do uwierzytelniania użytkownika przy użyciu członkostwa uwierzytelniania formularzy  
  
1.  Implementowanie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Poniższy kod przedstawia przykład <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementacji klasy okno dialogowe logowania pochodzące z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. To okno dialogowe zawiera pola tekstowe dla nazwy użytkownika i hasła oraz pole wyboru "Zapamiętaj mnie". Gdy wywołuje dostawcę uwierzytelniania klienta <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody formularza zostanie wyświetlony. Gdy użytkownik wprowadza informacje w oknie dialogowym logowania i kliknie przycisk OK, określone wartości są zwracane w ramach nowego <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> obiektu.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Wywołanie `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> — metoda i przekaż puste ciągi jako wartości parametrów. Po określeniu puste ciągi, ta metoda wewnętrznie wywołuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody dla dostawcy poświadczenia skonfigurowane dla aplikacji. Poniższy przykładowy kod wywołuje tę metodę, aby ograniczyć dostęp do całej aplikacji formularzy systemu Windows. Można dodać ten kod, aby <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obsługi.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Dostawca poświadczeń do uwierzytelniania bez użycia członkostwa użytkownika za pomocą uwierzytelniania formularzy  
  
-   Wywołanie `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> — metoda i Przekaż wartości nazwy i hasła użytkownika pobierane przez użytkownika.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Uwierzytelnianie użytkowników przy użyciu uwierzytelniania systemu Windows  
  
-   Wywołanie `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> — metoda i przekazać puste ciągi dla parametrów. Wywołanie tej metody zawsze zwraca `true` i spowoduje dodanie pliku cookie do pamięci podręcznej plików cookie użytkownika, który zawiera tożsamości systemu Windows.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przykładowy kod w tym temacie przedstawiono najprostszym użycia uwierzytelniania w aplikacji klienta systemu Windows. Podczas wywoływania `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody za pomocą aplikacji klienckiej usług i uwierzytelnianie formularzy, jednak może zgłosić kodu <xref:System.Net.WebException>. Oznacza to, że usługa uwierzytelniania jest niedostępny. Na przykład sposobu obsługi tego wyjątku zobacz [wskazówki: Korzystanie z usługi aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Przewodnik: używanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Korzystanie z uwierzytelniania formularzy z Microsoft Ajax](http://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
