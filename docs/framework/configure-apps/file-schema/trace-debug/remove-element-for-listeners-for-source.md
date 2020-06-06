---
title: <remove>Element dla <listeners> elementu<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/remove
helpviewer_keywords:
- remove element for <listeners> for <source>
- <remove> element for <listeners> for <source>
ms.assetid: 3ff6b578-273d-407f-b07f-8251f1f9f5d0
ms.openlocfilehash: 657e6db2af9b99b3bbf03afc6aab02c58a830f2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153338"
---
# <a name="remove-element-for-listeners-for-source"></a><span data-ttu-id="fdacb-102">\<remove>Element dla \<listeners> elementu\<source></span><span class="sxs-lookup"><span data-stu-id="fdacb-102">\<remove> Element for \<listeners> for \<source></span></span>
<span data-ttu-id="fdacb-103">Usuwa odbiornik z `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-103">Removes a listener from the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="fdacb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdacb-104">Syntax</span></span>  
  
```xml  
<remove name="listenerName" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdacb-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="fdacb-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fdacb-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="fdacb-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdacb-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="fdacb-107">Attributes</span></span>  
  
|<span data-ttu-id="fdacb-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="fdacb-108">Attribute</span></span>|<span data-ttu-id="fdacb-109">Opis</span><span class="sxs-lookup"><span data-stu-id="fdacb-109">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="fdacb-110">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="fdacb-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="fdacb-111">Nazwa odbiornika, który ma zostać usunięty z `Listeners` kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fdacb-111">The name of the listener to remove from the `Listeners` collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdacb-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="fdacb-112">Child Elements</span></span>  
 <span data-ttu-id="fdacb-113">Brak.</span><span class="sxs-lookup"><span data-stu-id="fdacb-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdacb-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="fdacb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fdacb-115">Element</span><span class="sxs-lookup"><span data-stu-id="fdacb-115">Element</span></span>|<span data-ttu-id="fdacb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="fdacb-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fdacb-117">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdacb-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="fdacb-118">Określa detektory śledzenia, które zbierają, przechowują i rozsyłają komunikaty oraz poziom, w którym ustawiono przełącznik śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="fdacb-119">Zawiera źródła śledzenia, które inicjują komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-119">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="fdacb-120">Określa źródło śledzenia, które inicjuje komunikaty śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-120">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="fdacb-121">Określa detektory, które zbierają, przechowują i rozsyłają komunikaty.</span><span class="sxs-lookup"><span data-stu-id="fdacb-121">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdacb-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdacb-122">Remarks</span></span>  
 <span data-ttu-id="fdacb-123">`<remove>`Element usuwa określony odbiornik z `Listeners` kolekcji dla źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-123">The `<remove>` element removes a specified listener from the `Listeners` collection for a trace source.</span></span>  
  
 <span data-ttu-id="fdacb-124">Można usunąć element z `Listeners` kolekcji dla źródła śledzenia programowo, wywołując <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> metodę we <xref:System.Diagnostics.TraceSource.Listeners%2A> właściwości <xref:System.Diagnostics.TraceSource> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="fdacb-124">You can remove an element from the `Listeners` collection for a trace source programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Remove%2A> method on the <xref:System.Diagnostics.TraceSource.Listeners%2A> property of the <xref:System.Diagnostics.TraceSource> instance.</span></span>  
  
 <span data-ttu-id="fdacb-125">Ten element może być używany w pliku konfiguracji komputera (Machine. config) i w pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdacb-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdacb-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdacb-126">Example</span></span>  
 <span data-ttu-id="fdacb-127">Poniższy przykład pokazuje, jak używać `<remove>` elementu przed użyciem `<add>` elementu, aby dodać odbiornik `console` do `Listeners` kolekcji dla źródła śledzenia `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="fdacb-127">The following example shows how to use the `<remove>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch" >  
         <listeners>  
           <remove name="Default"/>  
           <add name="console"
             type="System.Diagnostics.ConsoleTraceListener" />  
         </listeners>  
      </source>  
    </sources>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="fdacb-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fdacb-128">See also</span></span>

- <xref:System.Diagnostics.TraceSource.Listeners%2A>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="fdacb-129">Schemat ustawień śledzenia i debugowania</span><span class="sxs-lookup"><span data-stu-id="fdacb-129">Trace and Debug Settings Schema</span></span>](index.md)
- [\<clear>](clear-element-for-listeners-for-source.md)
- [<span data-ttu-id="fdacb-130">Obiekty nasłuchujące śledzenia</span><span class="sxs-lookup"><span data-stu-id="fdacb-130">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
