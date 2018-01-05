---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ffca9a587bdb32afc252f9719eb35e3139dd3f8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="7526a-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="7526a-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="7526a-103">Uzgadnianie zabezpieczeń z potencjalnych sąsiada zakończyła się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="7526a-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="7526a-104">Opis</span><span class="sxs-lookup"><span data-stu-id="7526a-104">Description</span></span>  
 <span data-ttu-id="7526a-105">Ślad występuje podczas próby ustanowienia połączenia z elementem sąsiednim bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="7526a-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="7526a-106">Może to nastąpić z powodu niewystarczających lub nieprawidłowe poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="7526a-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="7526a-107">PeerChannel rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają oparty na typie uwierzytelniania i autoryzacji, które można wdrożyć modelu silnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7526a-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="7526a-108">PeerChannel także zapewnia obsługę proste aplikacje przy użyciu hasła.</span><span class="sxs-lookup"><span data-stu-id="7526a-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="7526a-109">Hasła mogą być wykorzystywane tylko w celu wprowadzania z sesją; Nie można ich używany do uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="7526a-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="7526a-110">Jest to spowodowane tokenu symetrycznego, który udział grupy elementów równorzędnych jest trudne i nieodpowiednie do użycia na potrzeby uwierzytelniania źródła.</span><span class="sxs-lookup"><span data-stu-id="7526a-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="7526a-111">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="7526a-111">Troubleshooting</span></span>  
 <span data-ttu-id="7526a-112">Sprawdź, czy wszystkie sąsiadów mają poświadczenia odpowiednich ustawień zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="7526a-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7526a-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7526a-113">See Also</span></span>  
 [<span data-ttu-id="7526a-114">Zabezpieczenia kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="7526a-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="7526a-115">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="7526a-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [<span data-ttu-id="7526a-116">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="7526a-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [<span data-ttu-id="7526a-117">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7526a-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
