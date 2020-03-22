---
title: Uzyskiwanie dostępu do usług sieci Web aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: ad616bd46f92261ec5ad6ae81d0db48138631ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349226"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="cd9df-102">Uzyskiwanie dostępu do usług sieci Web aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cd9df-102">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="cd9df-103">Obiekt `My.WebServices` udostępnia wystąpienie każdej usługi sieci Web, do którego odwołuje się bieżący projekt.</span><span class="sxs-lookup"><span data-stu-id="cd9df-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="cd9df-104">Każde wystąpienie jest tworzone na żądanie.</span><span class="sxs-lookup"><span data-stu-id="cd9df-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="cd9df-105">Dostęp do tych usług sieci Web `My.WebServices` można uzyskać za pośrednictwem właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd9df-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="cd9df-106">Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do którą uzyskuje dostęp właściwość.</span><span class="sxs-lookup"><span data-stu-id="cd9df-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="cd9df-107">Każda klasa, która <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> dziedziczy z jest usługą sieci Web.</span><span class="sxs-lookup"><span data-stu-id="cd9df-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="cd9df-108">Zadania</span><span class="sxs-lookup"><span data-stu-id="cd9df-108">Tasks</span></span>

<span data-ttu-id="cd9df-109">W poniższej tabeli wymieniono możliwe sposoby uzyskiwania dostępu do usług sieci Web, do których odwołuje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="cd9df-109">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="cd9df-110">Do</span><span class="sxs-lookup"><span data-stu-id="cd9df-110">To</span></span>|<span data-ttu-id="cd9df-111">Zobacz</span><span class="sxs-lookup"><span data-stu-id="cd9df-111">See</span></span>|
|---|---|
|<span data-ttu-id="cd9df-112">Wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="cd9df-112">Call a Web service</span></span>|[<span data-ttu-id="cd9df-113">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="cd9df-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="cd9df-114">Wywoływanie usługi sieci Web asynchronicznie i obsługa zdarzenia po jego zakończeniu</span><span class="sxs-lookup"><span data-stu-id="cd9df-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="cd9df-115">Instrukcje: asynchroniczne wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="cd9df-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="cd9df-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd9df-116">See also</span></span>

- [<span data-ttu-id="cd9df-117">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="cd9df-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
