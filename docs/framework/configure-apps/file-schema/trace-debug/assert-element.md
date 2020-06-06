---
title: <assert> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088946"
---
# <a name="assert-element"></a><span data-ttu-id="541d0-102">\<assert> Element</span><span class="sxs-lookup"><span data-stu-id="541d0-102">\<assert> Element</span></span>
<span data-ttu-id="541d0-103">Określa, czy podczas wywoływania metody ma być wyświetlane okno komunikatu <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> , a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="541d0-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**

## <a name="syntax"></a><span data-ttu-id="541d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="541d0-104">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="541d0-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="541d0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="541d0-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="541d0-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="541d0-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="541d0-107">Attributes</span></span>  
  
|<span data-ttu-id="541d0-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="541d0-108">Attribute</span></span>|<span data-ttu-id="541d0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="541d0-109">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="541d0-110">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="541d0-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="541d0-111">Określa, czy ma być wyświetlane okno komunikatu, gdy metoda **Debug. Assert** zwraca **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="541d0-111">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="541d0-112">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="541d0-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="541d0-113">Określa nazwę pliku, do którego ma zostać zapisany komunikat, jeśli **Debug. Assert** zwraca **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="541d0-113">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="541d0-114">AssertUiEnabled — atrybut</span><span class="sxs-lookup"><span data-stu-id="541d0-114">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="541d0-115">Wartość</span><span class="sxs-lookup"><span data-stu-id="541d0-115">Value</span></span>|<span data-ttu-id="541d0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="541d0-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="541d0-117">Wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="541d0-117">Displays the message box.</span></span> <span data-ttu-id="541d0-118">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="541d0-118">This is the default.</span></span>|  
|`false`|<span data-ttu-id="541d0-119">Nie wyświetla okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="541d0-119">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="541d0-120">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="541d0-120">Child Elements</span></span>  
 <span data-ttu-id="541d0-121">Brak.</span><span class="sxs-lookup"><span data-stu-id="541d0-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="541d0-122">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="541d0-122">Parent Elements</span></span>  
  
|<span data-ttu-id="541d0-123">Element</span><span class="sxs-lookup"><span data-stu-id="541d0-123">Element</span></span>|<span data-ttu-id="541d0-124">Opis</span><span class="sxs-lookup"><span data-stu-id="541d0-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="541d0-125">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="541d0-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="541d0-126">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="541d0-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="541d0-127">Uwagi</span><span class="sxs-lookup"><span data-stu-id="541d0-127">Remarks</span></span>  
 <span data-ttu-id="541d0-128">Oba atrybuty w **\<assert>** elemencie są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="541d0-128">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="541d0-129">Można wyłączyć okna komunikatów bez określania pliku, w którym mają zostać zapisane komunikaty, lub można określić plik, do którego mają być zapisane komunikaty, pozostawiając pola komunikatów włączone.</span><span class="sxs-lookup"><span data-stu-id="541d0-129">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="541d0-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="541d0-130">Example</span></span>  
 <span data-ttu-id="541d0-131">Poniższy przykład pokazuje, jak wyłączyć wyświetlanie okien komunikatów po wywołaniu **debugowania. Assert** i Zapisz wiadomości w `c:\log.txt` .</span><span class="sxs-lookup"><span data-stu-id="541d0-131">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="541d0-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="541d0-132">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="541d0-133">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="541d0-133">Trace and Debug Settings Schema</span></span>](index.md)
