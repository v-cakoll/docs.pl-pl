---
title: Zasoby systemu operacyjnego wymagane przez architekturę WCF
ms.date: 03/30/2017
ms.assetid: cdd9a331-53fe-4e0d-bdfe-782264aec5c9
ms.openlocfilehash: c2c26d769424a8d0655591cb10b4b13df8a15884
ms.sourcegitcommit: 9b2ef64c4fc10a4a10f28a223d60d17d7d249ee8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/26/2019
ms.locfileid: "72961132"
---
# <a name="operating-system-resources-required-by-wcf"></a><span data-ttu-id="cab8f-102">Zasoby systemu operacyjnego wymagane przez architekturę WCF</span><span class="sxs-lookup"><span data-stu-id="cab8f-102">Operating System Resources Required by WCF</span></span>

<span data-ttu-id="cab8f-103">Windows Communication Foundation (WCF) zależy od kilku zasobów dostarczonych przez system operacyjny do działania.</span><span class="sxs-lookup"><span data-stu-id="cab8f-103">Windows Communication Foundation (WCF) depends on several resources that are provided by the operating system to function.</span></span> <span data-ttu-id="cab8f-104">W poniższej tabeli wymieniono te zasoby:</span><span class="sxs-lookup"><span data-stu-id="cab8f-104">The following table lists those resources:</span></span>

|<span data-ttu-id="cab8f-105">Zasób</span><span class="sxs-lookup"><span data-stu-id="cab8f-105">Resource</span></span>|<span data-ttu-id="cab8f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="cab8f-106">Description</span></span>|
|--------------|-----------------|
|<span data-ttu-id="cab8f-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span><span class="sxs-lookup"><span data-stu-id="cab8f-107">Microsoft Distributed Transaction Coordinator (MSDTC)</span></span>|<span data-ttu-id="cab8f-108">Wymagane do obsługi transakcji OleTx.</span><span class="sxs-lookup"><span data-stu-id="cab8f-108">Required to support OleTx transactions.</span></span>|
|<span data-ttu-id="cab8f-109">Internet Information Services (IIS)</span><span class="sxs-lookup"><span data-stu-id="cab8f-109">Internet Information Services (IIS)</span></span>|<span data-ttu-id="cab8f-110">Wymagane, jeśli chcesz używać usług IIS do hostowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cab8f-110">Required if you want to use IIS to host your application.</span></span>|
|<span data-ttu-id="cab8f-111">Usługa aktywacji procesów systemu Windows (WAS)</span><span class="sxs-lookup"><span data-stu-id="cab8f-111">Windows Process Activation Service (WAS)</span></span>|<span data-ttu-id="cab8f-112">Wymagane, jeśli chcesz używać aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cab8f-112">Required if you want to use WAS to host your application.</span></span>|
