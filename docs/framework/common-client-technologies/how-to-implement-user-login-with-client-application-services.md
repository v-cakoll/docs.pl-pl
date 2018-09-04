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
ms.openlocfilehash: a878b12620faf9a6e9fecbd2e76644aea3d80611
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504799"
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Porady: implementowanie logowania użytkownika przy użyciu usług aplikacji klienta
Usługi aplikacji klienta można użyć do weryfikowania użytkowników za pomocą istniejącego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi. Aby uzyskać informacje dotyczące sposobu konfigurowania [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] profilu usługi, zobacz [za pomocą uwierzytelniania formularzy z Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 W poniższych procedurach opisano sposób sprawdzania poprawności użytkowników za pośrednictwem usługi uwierzytelniania, gdy aplikacja jest skonfigurowana do korzystania z jednego dostawcy usług uwierzytelniania klienta. Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie usług aplikacji klienta](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Zwykle będzie wykonywać wszystkie weryfikacji za pomocą `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody. Ta metoda umożliwia zarządzanie interakcji z usługą uwierzytelniania za pośrednictwem dostawcy uwierzytelniania skonfigurowanego. Aby uzyskać więcej informacji, zobacz [przegląd usług aplikacji klienta](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Procedury uwierzytelniania formularzy wymagają dostępu do działającego [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] usługi uwierzytelniania. Aby uzyskać wskazówki dotyczące end-to-end testowanie aplikacji klienckiej usług funkcji, zobacz [Instruktaż: przy użyciu usług aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>Do uwierzytelnienia użytkownika za pomocą uwierzytelniania formularzy przy użyciu członkostwa dostawcy poświadczeń  
  
1.  Implementowanie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> interfejsu. Poniższy kod przedstawia przykład <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementacji klasy okno dialogowe logowania pochodzące z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. To okno dialogowe zawiera pola tekstowe nazwy użytkownika i hasła oraz pola wyboru "Zapamiętaj mnie". Gdy dostawca uwierzytelniania klient wywołuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody formularza jest wyświetlana. Po użytkownik wprowadza informacje w oknie dialogowym logowania i kliknie przycisk OK, określone wartości są zwracane w nowym <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> obiektu.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Wywołaj `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody i przekaż puste ciągi jako wartości parametrów. Po określeniu puste ciągi, ta metoda wywołuje wewnętrznie <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metody dla dostawcy poświadczenia skonfigurowane dla twojej aplikacji. Poniższy kod wywołuje tę metodę, aby ograniczyć dostęp do całej aplikacji Windows Forms. Można dodać ten kod w celu <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> programu obsługi.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>Dostawca poświadczeń do uwierzytelniania użytkowników za pomocą uwierzytelniania formularzy bez korzystania z członkostwa  
  
-   Wywołaj `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody i przekazać wartości nazwy i hasła użytkownika są pobierane przez użytkownika.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>Do uwierzytelnienia użytkownika za pomocą uwierzytelniania Windows  
  
-   Wywołaj `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody i przekazać puste ciągi dla parametrów. Wywołanie tej metody zawsze zwraca `true` i doda pliku cookie do pamięci podręcznej plików cookie przez użytkownika, który zawiera tożsamości Windows.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 Przykładowy kod w tym temacie pokazano najprostsze sposoby użycia uwierzytelniania w aplikacji klienckiej Windows. Gdy wywołujesz `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody za pomocą aplikacji klienckiej usługi oraz uwierzytelnianie formularzy, jednak Twój kod może zgłosić <xref:System.Net.WebException>. Oznacza to, że usługa uwierzytelniania jest niedostępna. Na przykład sposobu obsługi tego wyjątku zobacz [Instruktaż: przy użyciu usług aplikacji klienta](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Omówienie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Instrukcje: konfigurowanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Przewodnik: używanie usług aplikacji klienckich](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Korzystanie z uwierzytelniania formularzy z Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
