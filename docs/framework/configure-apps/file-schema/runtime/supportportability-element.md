---
title: '&lt;supportportability —&gt; — Element'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4f1ceae32445fb350f6fcc98f3a1eec044fa7885
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655507"
---
# <a name="ltsupportportabilitygt-element"></a><span data-ttu-id="82b6d-102">&lt;supportportability —&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-102">&lt;supportPortability&gt; Element</span></span>
<span data-ttu-id="82b6d-103">Określa, czy aplikacja może odwołać się tego samego zestawu w dwóch różnych implementacjach systemu .NET Framework, wyłączając zachowania domyślne, które traktuje zestawy za równorzędne do celów przenoszenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="82b6d-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
 <span data-ttu-id="82b6d-104">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-104">\<configuration> Element</span></span>  
<span data-ttu-id="82b6d-105">\<środowisko uruchomieniowe > Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-105">\<runtime> Element</span></span>  
<span data-ttu-id="82b6d-106">\<assemblybinding — > Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-106">\<assemblyBinding> Element</span></span>  
<span data-ttu-id="82b6d-107">\<supportPortability> Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-107">\<supportPortability> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b6d-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="82b6d-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82b6d-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="82b6d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="82b6d-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="82b6d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82b6d-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="82b6d-111">Attributes</span></span>  
  
|<span data-ttu-id="82b6d-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="82b6d-112">Attribute</span></span>|<span data-ttu-id="82b6d-113">Opis</span><span class="sxs-lookup"><span data-stu-id="82b6d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82b6d-114">PKT</span><span class="sxs-lookup"><span data-stu-id="82b6d-114">PKT</span></span>|<span data-ttu-id="82b6d-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="82b6d-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="82b6d-116">Określa publiczny klucz tokena dotkniętego zestawu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="82b6d-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="82b6d-117">Włączone</span><span class="sxs-lookup"><span data-stu-id="82b6d-117">enabled</span></span>|<span data-ttu-id="82b6d-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="82b6d-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="82b6d-119">Określa, czy obsługa przenoszenia między implementacjami określonego zestawu .NET Framework powinien być włączony.</span><span class="sxs-lookup"><span data-stu-id="82b6d-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="82b6d-120">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="82b6d-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="82b6d-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="82b6d-121">Value</span></span>|<span data-ttu-id="82b6d-122">Opis</span><span class="sxs-lookup"><span data-stu-id="82b6d-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="82b6d-123">true</span><span class="sxs-lookup"><span data-stu-id="82b6d-123">true</span></span>|<span data-ttu-id="82b6d-124">Włącz obsługę przenoszenia między implementacjami określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82b6d-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="82b6d-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="82b6d-125">This is the default.</span></span>|  
|<span data-ttu-id="82b6d-126">false</span><span class="sxs-lookup"><span data-stu-id="82b6d-126">false</span></span>|<span data-ttu-id="82b6d-127">Wyłącz obsługę przenoszenia między implementacjami określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82b6d-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="82b6d-128">Umożliwia aplikacjom odwołanie się do wielu implementacjach określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="82b6d-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82b6d-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="82b6d-129">Child Elements</span></span>  
 <span data-ttu-id="82b6d-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="82b6d-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82b6d-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="82b6d-131">Parent Elements</span></span>  
  
|<span data-ttu-id="82b6d-132">Element</span><span class="sxs-lookup"><span data-stu-id="82b6d-132">Element</span></span>|<span data-ttu-id="82b6d-133">Opis</span><span class="sxs-lookup"><span data-stu-id="82b6d-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="82b6d-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="82b6d-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="82b6d-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="82b6d-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="82b6d-136">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="82b6d-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82b6d-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="82b6d-137">Remarks</span></span>  
 <span data-ttu-id="82b6d-138">Począwszy od [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], obsługa jest dostarczana automatycznie dla aplikacji, które mogą użyć jednego z dwóch wdrożeń systemu .NET Framework, na przykład implementacji .NET Framework lub .NET Framework do wdrożenia dodatku Silverlight.</span><span class="sxs-lookup"><span data-stu-id="82b6d-138">Beginning with the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="82b6d-139">Dwie implementacje określonego zestawu .NET Framework są postrzegane jako równoważne przez binder zestawu.</span><span class="sxs-lookup"><span data-stu-id="82b6d-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="82b6d-140">W niektórych scenariuszach ta funkcja przenoszenia aplikacji powoduje problemy.</span><span class="sxs-lookup"><span data-stu-id="82b6d-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="82b6d-141">W tych scenariuszach `<supportPortability>` element może być użyty, aby wyłączyć funkcję.</span><span class="sxs-lookup"><span data-stu-id="82b6d-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
 <span data-ttu-id="82b6d-142">Taki scenariusz jest to zespół, który ma odniesienia zarówno wykonania .NET Framework, jak i programu .NET Framework dla wdrożenia dodatku Silverlight ze szczególnym odniesieniem zespołu.</span><span class="sxs-lookup"><span data-stu-id="82b6d-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="82b6d-143">Na przykład projektant XAML, napisany w Windows Presentation Foundation (WPF) może być konieczne odwołać zarówno implementacje pulpitu WPF dla interfejsu użytkownika projektanta i podzbiór WPF, który znajduje się w implementacji programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="82b6d-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="82b6d-144">Domyślnie oddzielne odwołania spowodują błąd kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="82b6d-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="82b6d-145">Ten element wyłącza domyślne zachowanie i pozwala kompilacja osiągnąć sukces.</span><span class="sxs-lookup"><span data-stu-id="82b6d-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="82b6d-146">Aby kompilator mógł przekazać informacje do logiki związanej z zestawem wykonywalnych języka wspólnego, należy użyć `/appconfig` opcję kompilatora, aby określić lokalizację pliku app.config, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="82b6d-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82b6d-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="82b6d-147">Example</span></span>  
 <span data-ttu-id="82b6d-148">Poniższy przykład umożliwia aplikacjom odwołanie się do wdrożenia programu .NET Framework i .NET Framework do wdrożenia dodatku Silverlight dowolnego zestawu .NET Framework, która znajduje się w obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="82b6d-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="82b6d-149">`/appconfig` — Opcja kompilatora musi służyć do określania lokalizacji tego pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="82b6d-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="82b6d-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82b6d-150">See also</span></span>
- [<span data-ttu-id="82b6d-151">/ AppConfig (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="82b6d-151">/appconfig (C# Compiler Options)</span></span>](../../../../../docs/csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [<span data-ttu-id="82b6d-152">Przegląd ujednolicenia zestawów programu .NET framework</span><span class="sxs-lookup"><span data-stu-id="82b6d-152">.NET Framework Assembly Unification Overview</span></span>](https://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
