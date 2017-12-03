---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3bfe7547fafb17503c972646d344263117d9d86
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="39547-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="39547-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="39547-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="39547-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="39547-104">ID</span><span class="sxs-lookup"><span data-stu-id="39547-104">ID</span></span>|<span data-ttu-id="39547-105">4208</span><span class="sxs-lookup"><span data-stu-id="39547-105">4208</span></span>|  
|<span data-ttu-id="39547-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="39547-106">Keywords</span></span>|<span data-ttu-id="39547-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="39547-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="39547-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="39547-108">Level</span></span>|<span data-ttu-id="39547-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="39547-109">Information</span></span>|  
|<span data-ttu-id="39547-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="39547-110">Channel</span></span>|<span data-ttu-id="39547-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="39547-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="39547-112">Opis</span><span class="sxs-lookup"><span data-stu-id="39547-112">Description</span></span>  
 <span data-ttu-id="39547-113">Wskazuje, że dostawca SQL jest ponownych prób wykonania polecenia SQL z powodu błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="39547-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="39547-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="39547-114">Message</span></span>  
 <span data-ttu-id="39547-115">Ponownych prób wykonania polecenia SQL z powodu błędu SQL numer %1.</span><span class="sxs-lookup"><span data-stu-id="39547-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="39547-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="39547-116">Details</span></span>  
  
|<span data-ttu-id="39547-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="39547-117">Data Item Name</span></span>|<span data-ttu-id="39547-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="39547-118">Data Item Type</span></span>|<span data-ttu-id="39547-119">Opis</span><span class="sxs-lookup"><span data-stu-id="39547-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="39547-120">Numer_błędu</span><span class="sxs-lookup"><span data-stu-id="39547-120">ErrorNumber</span></span>|<span data-ttu-id="39547-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="39547-121">xs:string</span></span>|<span data-ttu-id="39547-122">Numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="39547-122">The SQL error number.</span></span>|  
|<span data-ttu-id="39547-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="39547-123">AppDomain</span></span>|<span data-ttu-id="39547-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="39547-124">xs:string</span></span>|<span data-ttu-id="39547-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="39547-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
