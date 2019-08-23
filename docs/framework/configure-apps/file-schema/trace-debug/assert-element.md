---
title: <assert>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: 5ba781598542d271f41476b1a1e9d61faeb6ff74
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927183"
---
# <a name="assert-element"></a><span data-ttu-id="9eac4-102">\<Element Assert ></span><span class="sxs-lookup"><span data-stu-id="9eac4-102">\<assert> Element</span></span>
<span data-ttu-id="9eac4-103">Określa, czy podczas wywoływania <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody ma być wyświetlane okno komunikatu, a także określa nazwę pliku, w którym mają zostać zapisane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="9eac4-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="9eac4-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="9eac4-104">\<configuration></span></span>  
<span data-ttu-id="9eac4-105">\<system.diagnostics></span><span class="sxs-lookup"><span data-stu-id="9eac4-105">\<system.diagnostics></span></span>  
<span data-ttu-id="9eac4-106">\<> potwierdzenia</span><span class="sxs-lookup"><span data-stu-id="9eac4-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eac4-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="9eac4-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9eac4-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9eac4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9eac4-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9eac4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9eac4-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9eac4-110">Attributes</span></span>  
  
|<span data-ttu-id="9eac4-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9eac4-111">Attribute</span></span>|<span data-ttu-id="9eac4-112">Opis</span><span class="sxs-lookup"><span data-stu-id="9eac4-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="9eac4-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9eac4-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9eac4-114">Określa, czy ma być wyświetlane okno komunikatu, gdy metoda **Debug. Assert** zwraca **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="9eac4-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="9eac4-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="9eac4-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="9eac4-116">Określa nazwę pliku, do którego ma zostać zapisany komunikat, jeśli **Debug. Assert** zwraca **wartość false**.</span><span class="sxs-lookup"><span data-stu-id="9eac4-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="9eac4-117">AssertUiEnabled — atrybut</span><span class="sxs-lookup"><span data-stu-id="9eac4-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="9eac4-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="9eac4-118">Value</span></span>|<span data-ttu-id="9eac4-119">Opis</span><span class="sxs-lookup"><span data-stu-id="9eac4-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="9eac4-120">Wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9eac4-120">Displays the message box.</span></span> <span data-ttu-id="9eac4-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="9eac4-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="9eac4-122">Nie wyświetla okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="9eac4-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9eac4-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9eac4-123">Child Elements</span></span>  
 <span data-ttu-id="9eac4-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="9eac4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9eac4-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9eac4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="9eac4-126">Element</span><span class="sxs-lookup"><span data-stu-id="9eac4-126">Element</span></span>|<span data-ttu-id="9eac4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="9eac4-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9eac4-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9eac4-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="9eac4-129">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9eac4-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9eac4-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9eac4-130">Remarks</span></span>  
 <span data-ttu-id="9eac4-131">Oba atrybuty w  **\<elemencie Assert >** są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="9eac4-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="9eac4-132">Można wyłączyć okna komunikatów bez określania pliku, w którym mają zostać zapisane komunikaty, lub można określić plik, do którego mają być zapisane komunikaty, pozostawiając pola komunikatów włączone.</span><span class="sxs-lookup"><span data-stu-id="9eac4-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9eac4-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="9eac4-133">Example</span></span>  
 <span data-ttu-id="9eac4-134">Poniższy przykład pokazuje, jak wyłączyć wyświetlanie okien komunikatów po wywołaniu **debugowania. Assert** i Zapisz wiadomości w `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="9eac4-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9eac4-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9eac4-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="9eac4-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="9eac4-136">Trace and Debug Settings Schema</span></span>](index.md)
