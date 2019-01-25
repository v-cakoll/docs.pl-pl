---
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 1ed037c548f1d833f2a20118ee1e017cd19e3391
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628243"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="0ce5e-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="0ce5e-102">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>
<span data-ttu-id="0ce5e-103">Uzgadnianie zabezpieczeń z potencjalnymi sąsiadem nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-103">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="0ce5e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="0ce5e-104">Description</span></span>  
 <span data-ttu-id="0ce5e-105">Ślad występuje podczas próby ustanowienia połączenia sąsiada bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-105">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="0ce5e-106">Można to zrobić ze względu na niewystarczające lub niepoprawne poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-106">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="0ce5e-107">PeerChannel rozpoznaje jeden typ tokenu do identyfikacji silne certyfikatów X.509, które dostarczają modelu silna tożsamość na podstawie typu uwierzytelniania i autoryzacji, które można zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-107">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="0ce5e-108">PeerChannel zapewnia również obsługę prostej aplikacji przy użyciu hasła.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-108">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="0ce5e-109">Hasła mogą być wykorzystywane tylko w celu wprowadzania do sesji; one nie można przeprowadzić uwierzytelniania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-109">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="0ce5e-110">Jest to spowodowane to token symetryczny udziale, do grupy obiektów równorzędnych, jest trudne i nieodpowiednich treści na potrzeby uwierzytelniania źródła.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-110">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="0ce5e-111">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="0ce5e-111">Troubleshooting</span></span>  
 <span data-ttu-id="0ce5e-112">Upewnij się, że wszystkie sąsiadów poświadczenia odpowiednie zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="0ce5e-112">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ce5e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0ce5e-113">See also</span></span>
- [<span data-ttu-id="0ce5e-114">Zabezpieczenia kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="0ce5e-114">Peer Channel Security</span></span>](../../../../../docs/framework/wcf/feature-details/peer-channel-security.md)
- [<span data-ttu-id="0ce5e-115">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="0ce5e-115">Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="0ce5e-116">Rozwiązywanie problemów z aplikacją za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="0ce5e-116">Using Tracing to Troubleshoot Your Application</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="0ce5e-117">Administracja i diagnostyka</span><span class="sxs-lookup"><span data-stu-id="0ce5e-117">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
