---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252070"
---
# \<claimType>
<span data-ttu-id="02433-101">Określa jedno opcjonalne lub wymagane żądanie dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="02433-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="02433-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="02433-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02433-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="02433-103">Attributes and Elements</span></span>  
 <span data-ttu-id="02433-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="02433-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02433-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="02433-105">Attributes</span></span>  
  
|<span data-ttu-id="02433-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="02433-106">Attribute</span></span>|<span data-ttu-id="02433-107">Opis</span><span class="sxs-lookup"><span data-stu-id="02433-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="02433-108">typ</span><span class="sxs-lookup"><span data-stu-id="02433-108">type</span></span>|<span data-ttu-id="02433-109">Typ zgłoszenia.</span><span class="sxs-lookup"><span data-stu-id="02433-109">The claim type.</span></span> <span data-ttu-id="02433-110">Zwykle jest to identyfikator URI.</span><span class="sxs-lookup"><span data-stu-id="02433-110">Typically a URI.</span></span> <span data-ttu-id="02433-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="02433-111">Required.</span></span>|  
|<span data-ttu-id="02433-112">optional</span><span class="sxs-lookup"><span data-stu-id="02433-112">optional</span></span>|<span data-ttu-id="02433-113">Wartość logiczna określająca, czy typ zgłoszenia jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="02433-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="02433-114">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="02433-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02433-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="02433-115">Child Elements</span></span>  
 <span data-ttu-id="02433-116">Brak</span><span class="sxs-lookup"><span data-stu-id="02433-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="02433-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="02433-117">Parent Elements</span></span>  
  
|<span data-ttu-id="02433-118">Element</span><span class="sxs-lookup"><span data-stu-id="02433-118">Element</span></span>|<span data-ttu-id="02433-119">Opis</span><span class="sxs-lookup"><span data-stu-id="02433-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="02433-120">Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="02433-120">Specifies the set of required claims for incoming security tokens.</span></span>|
