---
title: 440 — StartSignpostEvent1
ms.date: 03/30/2017
ms.assetid: 27b551b5-ae76-49f8-bab8-6300009eb4c1
ms.openlocfilehash: 4b2b6b0fa9df4725edd4929512eb1d7534d933b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774174"
---
# <a name="440---startsignpostevent1"></a><span data-ttu-id="6b273-102">440 — StartSignpostEvent1</span><span class="sxs-lookup"><span data-stu-id="6b273-102">440 - StartSignpostEvent1</span></span>
## <a name="properties"></a><span data-ttu-id="6b273-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6b273-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6b273-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="6b273-104">ID</span></span>|<span data-ttu-id="6b273-105">440</span><span class="sxs-lookup"><span data-stu-id="6b273-105">440</span></span>|  
|<span data-ttu-id="6b273-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="6b273-106">Keywords</span></span>|<span data-ttu-id="6b273-107">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="6b273-107">Troubleshooting</span></span>|  
|<span data-ttu-id="6b273-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="6b273-108">Level</span></span>|<span data-ttu-id="6b273-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="6b273-109">Information</span></span>|  
|<span data-ttu-id="6b273-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="6b273-110">Channel</span></span>|<span data-ttu-id="6b273-111">Microsoft-Windows-Application Server-Applications/Analytic</span><span class="sxs-lookup"><span data-stu-id="6b273-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="6b273-112">Opis</span><span class="sxs-lookup"><span data-stu-id="6b273-112">Description</span></span>  
 <span data-ttu-id="6b273-113">W śledzenie aktywności wskazuje, czy wiadomość została uruchomiona przekraczania granicy działania w wysyłać ani odbierać.</span><span class="sxs-lookup"><span data-stu-id="6b273-113">In activity tracing, indicates a message has started crossing an activity boundary in send or receive.</span></span>  
  
## <a name="message"></a><span data-ttu-id="6b273-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="6b273-114">Message</span></span>  
 <span data-ttu-id="6b273-115">Hranice aktivity</span><span class="sxs-lookup"><span data-stu-id="6b273-115">Activity boundary.</span></span>  
  
## <a name="details"></a><span data-ttu-id="6b273-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6b273-116">Details</span></span>  
  
|<span data-ttu-id="6b273-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="6b273-117">Data Item Name</span></span>|<span data-ttu-id="6b273-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="6b273-118">Data Item Type</span></span>|<span data-ttu-id="6b273-119">Opis</span><span class="sxs-lookup"><span data-stu-id="6b273-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="6b273-120">ExtendedData</span><span class="sxs-lookup"><span data-stu-id="6b273-120">ExtendedData</span></span>|`xs:string`|<span data-ttu-id="6b273-121">Nazwa działania.</span><span class="sxs-lookup"><span data-stu-id="6b273-121">The name of the activity.</span></span>|  
|<span data-ttu-id="6b273-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="6b273-122">AppDomain</span></span>|`xs:string`|<span data-ttu-id="6b273-123">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="6b273-123">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
