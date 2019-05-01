---
title: 4201 — EndSqlCommandExecute
ms.date: 03/30/2017
ms.assetid: ae0dbc15-f98c-4096-a8d9-fbe4dc36f1cd
ms.openlocfilehash: 75c1cdd10aca6b177911bd9d2f51468016eb9e15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774364"
---
# <a name="4201---endsqlcommandexecute"></a><span data-ttu-id="535fa-102">4201 — EndSqlCommandExecute</span><span class="sxs-lookup"><span data-stu-id="535fa-102">4201 - EndSqlCommandExecute</span></span>
## <a name="properties"></a><span data-ttu-id="535fa-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="535fa-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="535fa-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="535fa-104">ID</span></span>|<span data-ttu-id="535fa-105">4201</span><span class="sxs-lookup"><span data-stu-id="535fa-105">4201</span></span>|  
|<span data-ttu-id="535fa-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="535fa-106">Keywords</span></span>|<span data-ttu-id="535fa-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="535fa-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="535fa-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="535fa-108">Level</span></span>|<span data-ttu-id="535fa-109">Pełny</span><span class="sxs-lookup"><span data-stu-id="535fa-109">Verbose</span></span>|  
|<span data-ttu-id="535fa-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="535fa-110">Channel</span></span>|<span data-ttu-id="535fa-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="535fa-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="535fa-112">Opis</span><span class="sxs-lookup"><span data-stu-id="535fa-112">Description</span></span>  
 <span data-ttu-id="535fa-113">Wskazuje, że zakończono wykonywanie polecenia SQL.</span><span class="sxs-lookup"><span data-stu-id="535fa-113">Indicates a SQL command has finished executing.</span></span>  
  
## <a name="message"></a><span data-ttu-id="535fa-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="535fa-114">Message</span></span>  
 <span data-ttu-id="535fa-115">Kończy wykonywanie polecenia SQL: %1</span><span class="sxs-lookup"><span data-stu-id="535fa-115">End SQL command execution: %1</span></span>  
  
## <a name="details"></a><span data-ttu-id="535fa-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="535fa-116">Details</span></span>  
  
|<span data-ttu-id="535fa-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="535fa-117">Data Item Name</span></span>|<span data-ttu-id="535fa-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="535fa-118">Data Item Type</span></span>|<span data-ttu-id="535fa-119">Opis</span><span class="sxs-lookup"><span data-stu-id="535fa-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="535fa-120">Klasy SqlCommand</span><span class="sxs-lookup"><span data-stu-id="535fa-120">SqlCommand</span></span>|<span data-ttu-id="535fa-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="535fa-121">xs:string</span></span>|<span data-ttu-id="535fa-122">Polecenie SQL, który został wykonany.</span><span class="sxs-lookup"><span data-stu-id="535fa-122">The SQL command that was executed.</span></span>|  
|<span data-ttu-id="535fa-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="535fa-123">AppDomain</span></span>|<span data-ttu-id="535fa-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="535fa-124">xs:string</span></span>|<span data-ttu-id="535fa-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="535fa-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
