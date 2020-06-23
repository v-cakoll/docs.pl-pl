---
title: Zabezpieczenia transportu
description: Te odwołania służą do zrozumienia mechanizmów zabezpieczeń transportu w WFC, sposobie ich implementacji oraz ich opcji.
ms.date: 03/30/2017
ms.assetid: 86c94153-e48d-4539-b6cf-cd8060582e7f
ms.openlocfilehash: d39aa49906b79b9e12eecf04629080863719f986
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244754"
---
# <a name="transport-security"></a><span data-ttu-id="d5b5f-103">Zabezpieczenia transportu</span><span class="sxs-lookup"><span data-stu-id="d5b5f-103">Transport Security</span></span>
<span data-ttu-id="d5b5f-104">Zabezpieczenia transportu w Windows Communication Foundation (WCF) zależą od wybranego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-104">Transport security in Windows Communication Foundation (WCF) depends on the binding selected.</span></span> <span data-ttu-id="d5b5f-105">Transport, który implementuje powiązanie, określa rzeczywisty mechanizm zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-105">The transport that the binding implements determines the actual security mechanism.</span></span> <span data-ttu-id="d5b5f-106">W tematach w tej sekcji opisano zaimplementowane mechanizmy i ich opcje.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-106">The topics in this section explain the mechanisms that are implemented and their options.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5b5f-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d5b5f-107">In This Section</span></span>  
 [<span data-ttu-id="d5b5f-108">Przegląd zabezpieczeń transportu</span><span class="sxs-lookup"><span data-stu-id="d5b5f-108">Transport Security Overview</span></span>](transport-security-overview.md)  
 <span data-ttu-id="d5b5f-109">Wyjaśnia podstawowe informacje o zabezpieczeniach transportu w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-109">Explains the basics of transport security in WCF.</span></span>  
  
 [<span data-ttu-id="d5b5f-110">Zabezpieczenia transportu HTTP</span><span class="sxs-lookup"><span data-stu-id="d5b5f-110">HTTP Transport Security</span></span>](http-transport-security.md)  
 <span data-ttu-id="d5b5f-111">Wyjaśnia, w jaki sposób WCF implementuje SSL (SSL lub HTTPS).</span><span class="sxs-lookup"><span data-stu-id="d5b5f-111">Explains how WCF implements Secure Sockets Layer (SSL, or HTTPS).</span></span>  
  
 [<span data-ttu-id="d5b5f-112">Opis uwierzytelniania HTTP</span><span class="sxs-lookup"><span data-stu-id="d5b5f-112">Understanding HTTP Authentication</span></span>](understanding-http-authentication.md)  
 <span data-ttu-id="d5b5f-113">Opisuje schematy uwierzytelniania HTTP, takie jak Basic, Digest, NT LAN Manager (NTLM) i inne.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-113">Describes HTTP authentication schemes, such as Basic, Digest, NT LAN Manager (NTLM), and others.</span></span>  
  
 [<span data-ttu-id="d5b5f-114">Korzystanie z personifikacji z zabezpieczeniami transportu</span><span class="sxs-lookup"><span data-stu-id="d5b5f-114">Using Impersonation with Transport Security</span></span>](using-impersonation-with-transport-security.md)  
 <span data-ttu-id="d5b5f-115">Wyjaśnia pięć poziomów personifikacji, które są możliwe w przypadku trybu zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="d5b5f-115">Explains the five levels of impersonation that are possible with transport security mode.</span></span>  
  
 [<span data-ttu-id="d5b5f-116">Instrukcje: konfigurowanie portu z certyfikatem SSL</span><span class="sxs-lookup"><span data-stu-id="d5b5f-116">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)  
 <span data-ttu-id="d5b5f-117">Instruktaż przedstawia podstawy konfigurowania portu na komputerze z certyfikatem X. 509 na potrzeby zabezpieczeń protokołu SSL (transport).</span><span class="sxs-lookup"><span data-stu-id="d5b5f-117">Walks through the basics of configuring a port on a machine with an X.509 certificate for SSL (transport) security.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d5b5f-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="d5b5f-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a><span data-ttu-id="d5b5f-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d5b5f-119">Related Sections</span></span>  
 [<span data-ttu-id="d5b5f-120">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="d5b5f-120">Securing Services and Clients</span></span>](securing-services-and-clients.md)  
  
## <a name="see-also"></a><span data-ttu-id="d5b5f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5b5f-121">See also</span></span>

- [<span data-ttu-id="d5b5f-122">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="d5b5f-122">Programming WCF Security</span></span>](programming-wcf-security.md)
