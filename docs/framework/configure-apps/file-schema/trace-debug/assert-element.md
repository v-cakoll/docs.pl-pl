---
title: '&lt;asercja&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b15e569ff6e42298c0a1de02f77ab7c302c70d86
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154245"
---
# <a name="ltassertgt-element"></a><span data-ttu-id="c8770-102">&lt;asercja&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="c8770-102">&lt;assert&gt; Element</span></span>
<span data-ttu-id="c8770-103">Określa, czy należy wyświetlić okno komunikatu, gdy wywołujesz <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metody; określa także nazwę pliku do zapisywania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="c8770-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  
  
 <span data-ttu-id="c8770-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="c8770-104">\<configuration></span></span>  
<span data-ttu-id="c8770-105">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="c8770-105">\<system.diagnostics></span></span>  
<span data-ttu-id="c8770-106">\<asercja ></span><span class="sxs-lookup"><span data-stu-id="c8770-106">\<assert></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8770-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8770-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8770-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c8770-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c8770-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c8770-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8770-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c8770-110">Attributes</span></span>  
  
|<span data-ttu-id="c8770-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c8770-111">Attribute</span></span>|<span data-ttu-id="c8770-112">Opis</span><span class="sxs-lookup"><span data-stu-id="c8770-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="c8770-113">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c8770-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c8770-114">Określa, czy do wyświetlania komunikatu polu kiedy **Debug.Assert** daje w wyniku metody **false**.</span><span class="sxs-lookup"><span data-stu-id="c8770-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="c8770-115">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c8770-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c8770-116">Określa nazwę pliku do zapisu komunikatu if **Debug.Assert** daje w wyniku **false**.</span><span class="sxs-lookup"><span data-stu-id="c8770-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="c8770-117">assertuienabled atrybutu</span><span class="sxs-lookup"><span data-stu-id="c8770-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="c8770-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="c8770-118">Value</span></span>|<span data-ttu-id="c8770-119">Opis</span><span class="sxs-lookup"><span data-stu-id="c8770-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="c8770-120">Wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c8770-120">Displays the message box.</span></span> <span data-ttu-id="c8770-121">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c8770-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="c8770-122">Wyświetla okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="c8770-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8770-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c8770-123">Child Elements</span></span>  
 <span data-ttu-id="c8770-124">Brak.</span><span class="sxs-lookup"><span data-stu-id="c8770-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8770-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c8770-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c8770-126">Element</span><span class="sxs-lookup"><span data-stu-id="c8770-126">Element</span></span>|<span data-ttu-id="c8770-127">Opis</span><span class="sxs-lookup"><span data-stu-id="c8770-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c8770-128">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c8770-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="c8770-129">Określa obiektów nasłuchujących śledzenia zbierać, przechowywać i kierowanie komunikatów i poziom, którego ustawiono przełącznikiem śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c8770-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8770-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c8770-130">Remarks</span></span>  
 <span data-ttu-id="c8770-131">Oba atrybuty w  **\<asercja >** elementu są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="c8770-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="c8770-132">Okna komunikatów można wyłączyć bez określania pliku, aby pisać wiadomości do lub można określić plik do zapisu komunikaty, które otrzymało, pozostawiając komunikatu pola włączone.</span><span class="sxs-lookup"><span data-stu-id="c8770-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8770-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8770-133">Example</span></span>  
 <span data-ttu-id="c8770-134">Poniższy przykład pokazuje, jak wyłączyć wyświetlanie okien komunikatów podczas wywoływania **Debug.Assert** i pisania komunikatów do `c:\log.txt`.</span><span class="sxs-lookup"><span data-stu-id="c8770-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8770-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8770-135">See Also</span></span>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="c8770-136">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="c8770-136">Trace and Debug Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
