---
title: <supportPortability> Element
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 63c309a8a93c1d31ed8f73a495cf5154c3590d56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115655"
---
# <a name="supportportability-element"></a><span data-ttu-id="c2f1e-102">\<element > Tag supportportability</span><span class="sxs-lookup"><span data-stu-id="c2f1e-102">\<supportPortability> Element</span></span>
<span data-ttu-id="c2f1e-103">Określa, że aplikacja może odwoływać się do tego samego zestawu w dwóch różnych implementacjach .NET Framework, przez wyłączenie domyślnego zachowania, które traktuje zestawy jako równoważne do celów przenośności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-103">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>  
  
<span data-ttu-id="c2f1e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="c2f1e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2f1e-105">&nbsp;&nbsp;[ **\<środowiska uruchomieniowego >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2f1e-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c2f1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zestawubinding**](assemblybinding-element-for-runtime.md) ></span><span class="sxs-lookup"><span data-stu-id="c2f1e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="c2f1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tag supportportability >**</span><span class="sxs-lookup"><span data-stu-id="c2f1e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2f1e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="c2f1e-108">Syntax</span></span>  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2f1e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c2f1e-109">Attributes and Elements</span></span>  

<span data-ttu-id="c2f1e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2f1e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c2f1e-111">Attributes</span></span>  
  
|<span data-ttu-id="c2f1e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c2f1e-112">Attribute</span></span>|<span data-ttu-id="c2f1e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="c2f1e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2f1e-114">PKT</span><span class="sxs-lookup"><span data-stu-id="c2f1e-114">PKT</span></span>|<span data-ttu-id="c2f1e-115">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="c2f1e-116">Określa token klucza publicznego zestawu, którego to dotyczy, jako ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-116">Specifies the public key token of the affected assembly, as a string.</span></span>|  
|<span data-ttu-id="c2f1e-117">dostępny</span><span class="sxs-lookup"><span data-stu-id="c2f1e-117">enabled</span></span>|<span data-ttu-id="c2f1e-118">Atrybut opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-118">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c2f1e-119">Określa, czy obsługa przenośności między implementacjami określonego zestawu .NET Framework powinna być włączona.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-119">Specifies whether support for portability between implementations of the specified .NET Framework assembly should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c2f1e-120">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="c2f1e-120">enabled Attribute</span></span>  
  
|<span data-ttu-id="c2f1e-121">Wartość</span><span class="sxs-lookup"><span data-stu-id="c2f1e-121">Value</span></span>|<span data-ttu-id="c2f1e-122">Opis</span><span class="sxs-lookup"><span data-stu-id="c2f1e-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2f1e-123">true</span><span class="sxs-lookup"><span data-stu-id="c2f1e-123">true</span></span>|<span data-ttu-id="c2f1e-124">Włącz obsługę przenośności między implementacjami określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-124">Enable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="c2f1e-125">Domyślnie włączone.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-125">This is the default.</span></span>|  
|<span data-ttu-id="c2f1e-126">false</span><span class="sxs-lookup"><span data-stu-id="c2f1e-126">false</span></span>|<span data-ttu-id="c2f1e-127">Wyłącz obsługę przenośności między implementacjami określonego zestawu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-127">Disable support for portability between implementations of the specified .NET Framework assembly.</span></span> <span data-ttu-id="c2f1e-128">Dzięki temu aplikacja może mieć odwołania do wielu implementacji określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-128">This enables the application to have references to multiple implementations of the specified assembly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2f1e-129">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c2f1e-129">Child Elements</span></span>  

<span data-ttu-id="c2f1e-130">Brak.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2f1e-131">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c2f1e-131">Parent Elements</span></span>  
  
|<span data-ttu-id="c2f1e-132">Element</span><span class="sxs-lookup"><span data-stu-id="c2f1e-132">Element</span></span>|<span data-ttu-id="c2f1e-133">Opis</span><span class="sxs-lookup"><span data-stu-id="c2f1e-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c2f1e-134">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c2f1e-135">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-135">Contains information about assembly binding and garbage collection.</span></span>|  
|`assemblyBinding`|<span data-ttu-id="c2f1e-136">Zawiera informacje o przekierowaniu wersji zestawu i lokalizacji zestawów.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-136">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2f1e-137">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2f1e-137">Remarks</span></span>  

<span data-ttu-id="c2f1e-138">Począwszy od .NET Framework 4, pomoc techniczna jest świadczona automatycznie dla aplikacji, które mogą korzystać z jednej z dwóch implementacji .NET Framework, na przykład implementacji .NET Framework lub .NET Framework dla implementacji Silverlight.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-138">Beginning with the .NET Framework 4, support is automatically provided for applications that can use either of two implementations of the .NET Framework, for example either the .NET Framework implementation or the .NET Framework for Silverlight implementation.</span></span> <span data-ttu-id="c2f1e-139">Dwie implementacje określonego zestawu .NET Framework są uważane za równoważne przez spinacz zestawu.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-139">The two implementations of a particular .NET Framework assembly are seen as equivalent by the assembly binder.</span></span> <span data-ttu-id="c2f1e-140">W kilku scenariuszach ta funkcja przenośności aplikacji powoduje problemy.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-140">In a few scenarios, this application portability feature causes problems.</span></span> <span data-ttu-id="c2f1e-141">W tych scenariuszach element `<supportPortability>` może być używany do wyłączania funkcji.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-141">In those scenarios, the `<supportPortability>` element can be used to disable the feature.</span></span>  
  
<span data-ttu-id="c2f1e-142">Taki scenariusz jest zestawem, który musi odwoływać się zarówno do implementacji .NET Framework, jak i .NET Framework do implementacji Silverlight dla określonego zestawu odwołania.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-142">One such scenario is an assembly that has to reference both the .NET Framework implementation and the .NET Framework for Silverlight implementation of a particular reference assembly.</span></span> <span data-ttu-id="c2f1e-143">Na przykład Projektant XAML zapisany w Windows Presentation Foundation (WPF) może potrzebować odwoływać się zarówno do implementacji pulpitu WPF, interfejsu użytkownika projektanta, jak i podzbioru WPF, który jest zawarty w implementacji Silverlight.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-143">For example, a XAML designer written in Windows Presentation Foundation (WPF) might need to reference both the WPF Desktop implementation, for the designer's user interface, and the subset of WPF that is included in the Silverlight implementation.</span></span> <span data-ttu-id="c2f1e-144">Domyślnie oddzielne odwołania powodują wystąpienie błędu kompilatora, ponieważ powiązanie zestawu widzi dwa zestawy jako równoważne.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-144">By default, the separate references cause a compiler error, because assembly binding sees the two assemblies as equivalent.</span></span> <span data-ttu-id="c2f1e-145">Ten element wyłącza zachowanie domyślne i zezwala na pomyślne Kompilowanie.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-145">This element disables the default behavior, and allows compilation to succeed.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c2f1e-146">Aby kompilator przeszedł informacje do logiki wiązania zestawu środowiska uruchomieniowego języka wspólnego, należy użyć opcji kompilatora `/appconfig`, aby określić lokalizację pliku App. config, który zawiera ten element.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-146">In order for the compiler to pass the information to the common language runtime's assembly-binding logic, you must use the `/appconfig` compiler option to specify the location of the app.config file that contains this element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2f1e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2f1e-147">Example</span></span>  

<span data-ttu-id="c2f1e-148">Poniższy przykład umożliwia aplikacji odwoływanie się do implementacji .NET Framework i .NET Framework dla implementacji Silverlight dowolnego zestawu .NET Framework, który istnieje w obu implementacjach.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-148">The following example enables an application to have references to both the .NET Framework implementation and the .NET Framework for Silverlight implementation of any .NET Framework assembly that exists in both implementations.</span></span> <span data-ttu-id="c2f1e-149">Aby określić lokalizację pliku App. config, należy użyć opcji kompilatora `/appconfig`.</span><span class="sxs-lookup"><span data-stu-id="c2f1e-149">The `/appconfig` compiler option must be used to specify the location of this app.config file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c2f1e-150">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2f1e-150">See also</span></span>

- [<span data-ttu-id="c2f1e-151">-AppConfig (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="c2f1e-151">-appconfig (C# Compiler Options)</span></span>](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- <span data-ttu-id="c2f1e-152">[Przegląd dezjednoczenia zestawu .NET Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c2f1e-152">[.NET Framework Assembly Unification Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))</span></span>
