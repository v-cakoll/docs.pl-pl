---
title: 4208 - RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511600"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="63718-102">4208 - RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="63718-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="63718-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="63718-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63718-104">ID</span><span class="sxs-lookup"><span data-stu-id="63718-104">ID</span></span>|<span data-ttu-id="63718-105">4208</span><span class="sxs-lookup"><span data-stu-id="63718-105">4208</span></span>|  
|<span data-ttu-id="63718-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="63718-106">Keywords</span></span>|<span data-ttu-id="63718-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="63718-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="63718-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="63718-108">Level</span></span>|<span data-ttu-id="63718-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="63718-109">Information</span></span>|  
|<span data-ttu-id="63718-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="63718-110">Channel</span></span>|<span data-ttu-id="63718-111">Microsoft-Windows aplikacji debugowania serwera — aplikacje</span><span class="sxs-lookup"><span data-stu-id="63718-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="63718-112">Opis</span><span class="sxs-lookup"><span data-stu-id="63718-112">Description</span></span>  
 <span data-ttu-id="63718-113">Wskazuje, że dostawca SQL jest ponownych prób wykonania polecenia SQL z powodu błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="63718-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="63718-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="63718-114">Message</span></span>  
 <span data-ttu-id="63718-115">Ponownych prób wykonania polecenia SQL z powodu błędu SQL numer %1.</span><span class="sxs-lookup"><span data-stu-id="63718-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="63718-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="63718-116">Details</span></span>  
  
|<span data-ttu-id="63718-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="63718-117">Data Item Name</span></span>|<span data-ttu-id="63718-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="63718-118">Data Item Type</span></span>|<span data-ttu-id="63718-119">Opis</span><span class="sxs-lookup"><span data-stu-id="63718-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="63718-120">Numer_błędu</span><span class="sxs-lookup"><span data-stu-id="63718-120">ErrorNumber</span></span>|<span data-ttu-id="63718-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="63718-121">xs:string</span></span>|<span data-ttu-id="63718-122">Numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="63718-122">The SQL error number.</span></span>|  
|<span data-ttu-id="63718-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="63718-123">AppDomain</span></span>|<span data-ttu-id="63718-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="63718-124">xs:string</span></span>|<span data-ttu-id="63718-125">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="63718-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
