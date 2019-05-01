---
title: 4207 — MaximumRetriesExceededForSqlCommand
ms.date: 03/30/2017
ms.assetid: 8c8bee26-9ad4-4e01-bd16-0e1fd510fb6b
ms.openlocfilehash: b763e087d8ead2bcc0fadd1d0223ae1bd58c9fd9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774312"
---
# <a name="4207---maximumretriesexceededforsqlcommand"></a><span data-ttu-id="9a72b-102">4207 — MaximumRetriesExceededForSqlCommand</span><span class="sxs-lookup"><span data-stu-id="9a72b-102">4207 - MaximumRetriesExceededForSqlCommand</span></span>
## <a name="properties"></a><span data-ttu-id="9a72b-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9a72b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a72b-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="9a72b-104">ID</span></span>|<span data-ttu-id="9a72b-105">4207</span><span class="sxs-lookup"><span data-stu-id="9a72b-105">4207</span></span>|  
|<span data-ttu-id="9a72b-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="9a72b-106">Keywords</span></span>|<span data-ttu-id="9a72b-107">Limit przydziału, WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="9a72b-107">Quota, WFInstanceStore</span></span>|  
|<span data-ttu-id="9a72b-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="9a72b-108">Level</span></span>|<span data-ttu-id="9a72b-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="9a72b-109">Information</span></span>|  
|<span data-ttu-id="9a72b-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="9a72b-110">Channel</span></span>|<span data-ttu-id="9a72b-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="9a72b-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a72b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9a72b-112">Description</span></span>  
 <span data-ttu-id="9a72b-113">Wskazuje, że dostawcy bazy danych SQL rezygnacji ponowieniem uruchomienia polecenia SQL, ponieważ wykonano maksymalną liczbę ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="9a72b-113">Indicates SQL provider is giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a72b-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="9a72b-114">Message</span></span>  
 <span data-ttu-id="9a72b-115">Wykonano rezygnacji ponowieniem uruchomienia polecenia SQL jako maksymalną liczbę ponownych prób.</span><span class="sxs-lookup"><span data-stu-id="9a72b-115">Giving up retrying a SQL command as the maximum number of retries have been performed.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a72b-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="9a72b-116">Details</span></span>  
  
|<span data-ttu-id="9a72b-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="9a72b-117">Data Item Name</span></span>|<span data-ttu-id="9a72b-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="9a72b-118">Data Item Type</span></span>|<span data-ttu-id="9a72b-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9a72b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a72b-120">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a72b-120">AppDomain</span></span>|<span data-ttu-id="9a72b-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="9a72b-121">xs:string</span></span>|<span data-ttu-id="9a72b-122">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a72b-122">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
