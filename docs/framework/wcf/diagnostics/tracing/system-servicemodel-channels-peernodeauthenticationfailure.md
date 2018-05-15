---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 633f497950ab14d7715537eed8f5cc80e7a350a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="0ce2b-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="0ce2b-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="0ce2b-103">Uzgadnianie zabezpieczeń z potencjalnych sąsiada zakończyła się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ce2b-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0ce2b-104">Description</span></span>  
 <span data-ttu-id="0ce2b-105">Ślad występuje podczas próby ustanowienia połączenia z elementem sąsiednim bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="0ce2b-106">Może to nastąpić z powodu niewystarczających lub nieprawidłowe poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="0ce2b-107">PeerChannel rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają oparty na typie uwierzytelniania i autoryzacji, które można wdrożyć modelu silnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="0ce2b-108">PeerChannel także zapewnia obsługę proste aplikacje przy użyciu hasła.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="0ce2b-109">Hasła mogą być wykorzystywane tylko w celu wprowadzania z sesją; Nie można ich używany do uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="0ce2b-110">Jest to spowodowane tokenu symetrycznego, który udział grupy elementów równorzędnych jest trudne i nieodpowiednie do użycia na potrzeby uwierzytelniania źródła.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0ce2b-111">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0ce2b-111">Troubleshooting</span></span>  
 <span data-ttu-id="0ce2b-112">Sprawdź, czy wszystkie sąsiadów mają poświadczenia odpowiednich ustawień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0ce2b-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce2b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0ce2b-113">See Also</span></span>  
 [<span data-ttu-id="0ce2b-114">Zabezpieczenia kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="0ce2b-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="0ce2b-115">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0ce2b-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="0ce2b-116">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0ce2b-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="0ce2b-117">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0ce2b-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
