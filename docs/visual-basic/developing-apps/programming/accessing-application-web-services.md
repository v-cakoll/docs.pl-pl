---
title: Uzyskiwanie dostępu do usług internetowych aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- Web services [Visual Basic], My.WebServices object
- My.WebServices object
- applications [Visual Basic], Web services
ms.assetid: 8ad5405b-e771-42b1-82d3-ce97af2cea9e
ms.openlocfilehash: ad616bd46f92261ec5ad6ae81d0db48138631ed1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349226"
---
# <a name="accessing-application-web-services-visual-basic"></a><span data-ttu-id="4f252-102">Uzyskiwanie dostępu do usług sieci Web aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f252-102">Accessing Application Web Services (Visual Basic)</span></span>

<span data-ttu-id="4f252-103">Obiekt `My.WebServices` zapewnia wystąpienie każdej usługi sieci Web, do której odwołuje się bieżący projekt.</span><span class="sxs-lookup"><span data-stu-id="4f252-103">The `My.WebServices` object provides an instance of each Web service referenced by the current project.</span></span> <span data-ttu-id="4f252-104">Każde wystąpienie jest tworzone na żądanie.</span><span class="sxs-lookup"><span data-stu-id="4f252-104">Each instance is instantiated on demand.</span></span> <span data-ttu-id="4f252-105">Dostęp do tych usług sieci Web można uzyskać za pomocą właściwości obiektu `My.WebServices`.</span><span class="sxs-lookup"><span data-stu-id="4f252-105">You can access these Web services through the properties of the `My.WebServices` object.</span></span> <span data-ttu-id="4f252-106">Nazwa właściwości jest taka sama jak nazwa usługi sieci Web, do której uzyskuje dostęp właściwość.</span><span class="sxs-lookup"><span data-stu-id="4f252-106">The name of the property is the same as the name of the Web service that the property accesses.</span></span> <span data-ttu-id="4f252-107">Każda klasa, która dziedziczy po <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>, jest usługą sieci Web.</span><span class="sxs-lookup"><span data-stu-id="4f252-107">Any class that inherits from <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> is a Web service.</span></span>

## <a name="tasks"></a><span data-ttu-id="4f252-108">Zadania</span><span class="sxs-lookup"><span data-stu-id="4f252-108">Tasks</span></span>

<span data-ttu-id="4f252-109">W poniższej tabeli przedstawiono możliwe sposoby uzyskiwania dostępu do usług sieci Web, do których odwołuje się aplikacja.</span><span class="sxs-lookup"><span data-stu-id="4f252-109">The following table lists possible ways to access Web services referenced by an application.</span></span>

|<span data-ttu-id="4f252-110">Do</span><span class="sxs-lookup"><span data-stu-id="4f252-110">To</span></span>|<span data-ttu-id="4f252-111">Zobacz</span><span class="sxs-lookup"><span data-stu-id="4f252-111">See</span></span>|
|---|---|
|<span data-ttu-id="4f252-112">Wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="4f252-112">Call a Web service</span></span>|[<span data-ttu-id="4f252-113">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="4f252-113">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)|
|<span data-ttu-id="4f252-114">Wywołaj usługę sieci Web asynchronicznie i obsłuż zdarzenie po jego zakończeniu</span><span class="sxs-lookup"><span data-stu-id="4f252-114">Call a Web service asynchronously and handle an event when it completes</span></span>|[<span data-ttu-id="4f252-115">Instrukcje: asynchroniczne wywoływanie usługi sieci Web</span><span class="sxs-lookup"><span data-stu-id="4f252-115">How to: Call a Web Service Asynchronously</span></span>](../../../visual-basic/developing-apps/programming/how-to-call-a-web-service-asynchronously.md)|

## <a name="see-also"></a><span data-ttu-id="4f252-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f252-116">See also</span></span>

- [<span data-ttu-id="4f252-117">My.WebServices, obiekt</span><span class="sxs-lookup"><span data-stu-id="4f252-117">My.WebServices Object</span></span>](../../../visual-basic/language-reference/objects/my-webservices-object.md)
