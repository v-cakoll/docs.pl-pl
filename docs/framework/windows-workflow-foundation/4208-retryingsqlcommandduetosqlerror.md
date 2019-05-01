---
title: 4208 — RetryingSqlCommandDueToSqlError
ms.date: 03/30/2017
ms.assetid: a8e6483a-a6e4-4bbf-82ec-cd8b6e711aad
ms.openlocfilehash: a97336f12ccfe041b79328bcb48f4e7214a05b63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774299"
---
# <a name="4208---retryingsqlcommandduetosqlerror"></a><span data-ttu-id="25ada-102">4208 — RetryingSqlCommandDueToSqlError</span><span class="sxs-lookup"><span data-stu-id="25ada-102">4208 - RetryingSqlCommandDueToSqlError</span></span>
## <a name="properties"></a><span data-ttu-id="25ada-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="25ada-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25ada-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="25ada-104">ID</span></span>|<span data-ttu-id="25ada-105">4208</span><span class="sxs-lookup"><span data-stu-id="25ada-105">4208</span></span>|  
|<span data-ttu-id="25ada-106">słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="25ada-106">Keywords</span></span>|<span data-ttu-id="25ada-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="25ada-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="25ada-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="25ada-108">Level</span></span>|<span data-ttu-id="25ada-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="25ada-109">Information</span></span>|  
|<span data-ttu-id="25ada-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="25ada-110">Channel</span></span>|<span data-ttu-id="25ada-111">Microsoft-Windows-Application Server-Applications/Debug</span><span class="sxs-lookup"><span data-stu-id="25ada-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25ada-112">Opis</span><span class="sxs-lookup"><span data-stu-id="25ada-112">Description</span></span>  
 <span data-ttu-id="25ada-113">Wskazuje, że dostawcy bazy danych SQL jest ponowieniem uruchomienia polecenia SQL z powodu błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="25ada-113">Indicates the SQL provider is retrying a SQL command due to a SQL error.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25ada-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="25ada-114">Message</span></span>  
 <span data-ttu-id="25ada-115">Ponawianie próby za pomocą polecenia SQL ze względu na %1. numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="25ada-115">Retrying a SQL command due to SQL error number %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25ada-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="25ada-116">Details</span></span>  
  
|<span data-ttu-id="25ada-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="25ada-117">Data Item Name</span></span>|<span data-ttu-id="25ada-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="25ada-118">Data Item Type</span></span>|<span data-ttu-id="25ada-119">Opis</span><span class="sxs-lookup"><span data-stu-id="25ada-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25ada-120">ErrorNumber</span><span class="sxs-lookup"><span data-stu-id="25ada-120">ErrorNumber</span></span>|<span data-ttu-id="25ada-121">xs:String</span><span class="sxs-lookup"><span data-stu-id="25ada-121">xs:string</span></span>|<span data-ttu-id="25ada-122">Numer błędu SQL.</span><span class="sxs-lookup"><span data-stu-id="25ada-122">The SQL error number.</span></span>|  
|<span data-ttu-id="25ada-123">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25ada-123">AppDomain</span></span>|<span data-ttu-id="25ada-124">xs:String</span><span class="sxs-lookup"><span data-stu-id="25ada-124">xs:string</span></span>|<span data-ttu-id="25ada-125">Ciąg zwracany przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25ada-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
