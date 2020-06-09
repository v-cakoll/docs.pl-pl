---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: cb7019f1e4b47bde7c98b0109afa7b0125b7ef63
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84577308"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="54d00-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="54d00-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="54d00-103">Uzgadnianie zabezpieczeń z potencjalnym sąsiadem nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="54d00-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="54d00-104">Opis</span><span class="sxs-lookup"><span data-stu-id="54d00-104">Description</span></span>  
 <span data-ttu-id="54d00-105">Ten ślad występuje podczas próby nawiązania bezpiecznego połączenia sąsiada.</span><span class="sxs-lookup"><span data-stu-id="54d00-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="54d00-106">Przyczyną może być niewystarczające lub nieprawidłowe poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="54d00-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="54d00-107">PeerChannel rozpoznaje pojedynczy typ tokenu dla silnej identyfikacji, certyfikaty X. 509, które zapewniają silny model tożsamości na podstawie typu uwierzytelniania i autoryzacji, które mogą być implementowane.</span><span class="sxs-lookup"><span data-stu-id="54d00-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="54d00-108">PeerChannel zapewnia również obsługę prostych aplikacji przy użyciu haseł.</span><span class="sxs-lookup"><span data-stu-id="54d00-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="54d00-109">Haseł można używać tylko w celu zezwalania na wpis w sesji; nie można ich używać do uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="54d00-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="54d00-110">Jest to spowodowane tym, że symetryczny token, który jest używany przez grupę elementów równorzędnych, jest trudny i nieodpowiedni do uwierzytelniania źródłowego.</span><span class="sxs-lookup"><span data-stu-id="54d00-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="54d00-111">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="54d00-111">Troubleshooting</span></span>  
 <span data-ttu-id="54d00-112">Upewnij się, że wszystkie sąsiedzi mają odpowiednie poświadczenia zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="54d00-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54d00-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54d00-113">See also</span></span>

- [<span data-ttu-id="54d00-114">Zabezpieczenia kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="54d00-114">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="54d00-115">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="54d00-115">Tracing</span></span>](index.md)
- [<span data-ttu-id="54d00-116">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="54d00-116">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="54d00-117">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="54d00-117">Administration and Diagnostics</span></span>](../index.md)
