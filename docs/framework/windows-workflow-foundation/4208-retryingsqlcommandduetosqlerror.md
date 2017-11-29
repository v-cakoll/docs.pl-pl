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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01db76802b96bd32e8a01cf86b1e682defe97a06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="21ab1-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="21ab1-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="21ab1-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="21ab1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21ab1-104">ID</span><span class="sxs-lookup"><span data-stu-id="21ab1-104">ID</span></span>|<span data-ttu-id="21ab1-105">4208</span><span class="sxs-lookup"><span data-stu-id="21ab1-105">4208</span></span>|  
|<span data-ttu-id="21ab1-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="21ab1-106">Keywords</span></span>|<span data-ttu-id="21ab1-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="21ab1-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="21ab1-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="21ab1-108">Level</span></span>|<span data-ttu-id="21ab1-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="21ab1-109">Information</span></span>|  
|<span data-ttu-id="21ab1-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="21ab1-110">Channel</span></span>|<span data-ttu-id="21ab1-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="21ab1-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="21ab1-112">Opis</span><span class="sxs-lookup"><span data-stu-id="21ab1-112">Description</span></span>  
 <span data-ttu-id="21ab1-113">Wskazuje, że dostawca SQL jest ponownych prób wykonania polecenia SQL z powodu błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="21ab1-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="21ab1-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="21ab1-114">Message</span></span>  
 <span data-ttu-id="21ab1-115">Ponownych prób wykonania polecenia SQL z powodu błędu SQL numer %1.</span><span class="sxs-lookup"><span data-stu-id="21ab1-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="21ab1-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="21ab1-116">Details</span></span>  
  
|<span data-ttu-id="21ab1-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="21ab1-117">Data Item Name</span></span>|<span data-ttu-id="21ab1-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="21ab1-118">Data Item Type</span></span>|<span data-ttu-id="21ab1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="21ab1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="21ab1-120">Numer_błędu</span><span class="sxs-lookup"><span data-stu-id="21ab1-120">ErrorNumber</span></span>|<span data-ttu-id="21ab1-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="21ab1-121">xs:string</span></span>|<span data-ttu-id="21ab1-122">Numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="21ab1-122">The SQL error number.</span></span>|  
|<span data-ttu-id="21ab1-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="21ab1-123">AppDomain</span></span>|<span data-ttu-id="21ab1-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="21ab1-124">xs:string</span></span>|<span data-ttu-id="21ab1-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="21ab1-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
