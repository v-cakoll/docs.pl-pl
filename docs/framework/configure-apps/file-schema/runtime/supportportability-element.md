---
title: '&lt;supportPortability&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="50467-102">&lt;supportPortability&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="50467-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="50467-103">Określa, aplikacja może odwoływać tego samego zestawu w dwóch różnych implementacji programu .NET Framework, wyłączając domyślne zachowanie, która traktuje zestawy jako równoważne do celów przenośność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="50467-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="50467-104">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="50467-104">\<configuration> Element</span></span>  
<span data-ttu-id="50467-105">\<środowisko uruchomieniowe > — Element</span><span class="sxs-lookup"><span data-stu-id="50467-105">\<runtime> Element</span></span>  
<span data-ttu-id="50467-106">\<assemblybinding — > — Element</span><span class="sxs-lookup"><span data-stu-id="50467-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="50467-107">\<supportPortability > — Element</span><span class="sxs-lookup"><span data-stu-id="50467-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50467-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="50467-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="50467-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="50467-109">Attributes and Elements</span></span>  
 <span data-ttu-id="50467-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="50467-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="50467-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="50467-111">Attributes</span></span>  
  
|<span data-ttu-id="50467-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="50467-112">Attribute</span></span>|<span data-ttu-id="50467-113">Opis</span><span class="sxs-lookup"><span data-stu-id="50467-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="50467-114">PKT</span><span class="sxs-lookup"><span data-stu-id="50467-114">PKT</span></span>|<span data-ttu-id="50467-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="50467-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="50467-116">Określa token klucza publicznego zestawu wykorzystywanych jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="50467-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="50467-117">włączone</span><span class="sxs-lookup"><span data-stu-id="50467-117">enabled</span></span>|<span data-ttu-id="50467-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="50467-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="50467-119">Określa, czy można włączyć obsługę przenoszenia między implementacji określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50467-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="50467-120">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="50467-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="50467-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="50467-121">Value</span></span>|<span data-ttu-id="50467-122">Opis</span><span class="sxs-lookup"><span data-stu-id="50467-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="50467-123">true</span><span class="sxs-lookup"><span data-stu-id="50467-123">true</span></span>|<span data-ttu-id="50467-124">Włącz obsługę przenośności między implementacji określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50467-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="50467-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="50467-125">This is the default.</span></span>|  
|<span data-ttu-id="50467-126">false</span><span class="sxs-lookup"><span data-stu-id="50467-126">false</span></span>|<span data-ttu-id="50467-127">Wyłącz obsługę przenośności między implementacji określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50467-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="50467-128">Umożliwia to aplikacji odwołują się do wielu wdrożeń określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="50467-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="50467-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="50467-129">Child Elements</span></span>  
 <span data-ttu-id="50467-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="50467-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="50467-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="50467-131">Parent Elements</span></span>  
  
|<span data-ttu-id="50467-132">Element</span><span class="sxs-lookup"><span data-stu-id="50467-132">Element</span></span>|<span data-ttu-id="50467-133">Opis</span><span class="sxs-lookup"><span data-stu-id="50467-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="50467-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50467-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="50467-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="50467-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="50467-136">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="50467-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50467-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50467-137">Remarks</span></span>  
 <span data-ttu-id="50467-138">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], automatycznie podano pomocy technicznej dla aplikacji, które można użyć jednej z dwóch implementacji programu .NET Framework, na przykład albo wdrożenia programu .NET Framework lub .NET Framework dla programu Silverlight implementacji.</span><span class="sxs-lookup"><span data-stu-id="50467-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="50467-139">Dwa implementacji określonego zestawu .NET Framework są widoczne jako równoważne przez obiekt wiążący zestawu.</span><span class="sxs-lookup"><span data-stu-id="50467-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="50467-140">W kilka scenariuszy ta funkcja przenośność aplikacji powoduje występowanie problemów.</span><span class="sxs-lookup"><span data-stu-id="50467-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="50467-141">W tych scenariuszach `<supportPortability>` element może być użyty, aby wyłączyć tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="50467-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="50467-142">Taki scenariusz jest zestawem, aby odwoływać zarówno wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu danego odwołania.</span><span class="sxs-lookup"><span data-stu-id="50467-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="50467-143">Na przykład projektanta XAML zapisywane w systemie Windows Presentation Foundation (WPF) może być konieczne odwoływać zarówno w celu wykonania pulpitu WPF, dla interfejsu użytkownika projektanta i podzbiór WPF, który znajduje się w implementacji programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="50467-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="50467-144">Domyślnie wystąpi błąd kompilatora spowodować oddzielne odwołań, ponieważ powiązań zestawów będzie widział dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="50467-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="50467-145">Ten element wyłącza domyślne zachowanie i umożliwia kompilacja powiodła się.</span><span class="sxs-lookup"><span data-stu-id="50467-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="50467-146">Aby kompilator, aby przekazać informacje do środowiska CLR dla powiązania zestawu logiki, należy użyć `/appconfig` opcję kompilatora, aby określić lokalizację pliku app.config, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="50467-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50467-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="50467-147">Example</span></span>  
 <span data-ttu-id="50467-148">Poniższy przykład umożliwia aplikacji odwołują się do wdrożenia programu .NET Framework i programu .NET Framework dla programu Silverlight implementacji zestawu .NET Framework, który istnieje w obu wdrożeniach.</span><span class="sxs-lookup"><span data-stu-id="50467-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="50467-149">`/appconfig` — Opcja kompilatora może służyć do określania lokalizacja tego pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="50467-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="50467-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50467-150">See Also</span></span>  
 [<span data-ttu-id="50467-151">/ AppConfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="50467-151">/appconfig (C# Compiler Options)</span></span>](http://msdn.microsoft.com/library/ee523958.aspx)  
 [<span data-ttu-id="50467-152">Omówienie ujednolicenie programu .NET framework zestawu</span><span class="sxs-lookup"><span data-stu-id="50467-152">.NET Framework Assembly Unification Overview</span></span>](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
