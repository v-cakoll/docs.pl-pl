---
title: <disableFusionUpdatesFromADManager> Element
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
ms.openlocfilehash: 4e7375fddaa98b45766b29d911d555f773edcafa
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117444"
---
# <a name="disablefusionupdatesfromadmanager-element"></a><span data-ttu-id="7038e-102">\<disableFusionUpdatesFromADManager> Element</span><span class="sxs-lookup"><span data-stu-id="7038e-102">\<disableFusionUpdatesFromADManager> Element</span></span>
<span data-ttu-id="7038e-103">Określa, czy domyślne zachowanie, które umożliwia hostowi środowiska uruchomieniowego przesłonięcie ustawień konfiguracji dla domeny aplikacji, jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7038e-103">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableFusionUpdatesFromADManager>**  
  
## <a name="syntax"></a><span data-ttu-id="7038e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7038e-104">Syntax</span></span>  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7038e-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7038e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7038e-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7038e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7038e-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7038e-107">Attributes</span></span>  
  
|<span data-ttu-id="7038e-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7038e-108">Attribute</span></span>|<span data-ttu-id="7038e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7038e-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7038e-110">enabled</span><span class="sxs-lookup"><span data-stu-id="7038e-110">enabled</span></span>|<span data-ttu-id="7038e-111">Atrybut wymagany.</span><span class="sxs-lookup"><span data-stu-id="7038e-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7038e-112">Określa, czy domyślna możliwość przesłonięcia ustawień Fusion jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="7038e-112">Specifies whether the default ability to override Fusion settings is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="7038e-113">Atrybut włączony</span><span class="sxs-lookup"><span data-stu-id="7038e-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="7038e-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="7038e-114">Value</span></span>|<span data-ttu-id="7038e-115">Opis</span><span class="sxs-lookup"><span data-stu-id="7038e-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7038e-116">0</span><span class="sxs-lookup"><span data-stu-id="7038e-116">0</span></span>|<span data-ttu-id="7038e-117">Nie należy wyłączać możliwości przesłonięcia ustawień Fusion.</span><span class="sxs-lookup"><span data-stu-id="7038e-117">Do not disable the ability to override Fusion settings.</span></span> <span data-ttu-id="7038e-118">Jest to zachowanie domyślne, zaczynając od .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7038e-118">This is the default behavior, starting with the .NET Framework 4.</span></span>|  
|<span data-ttu-id="7038e-119">1</span><span class="sxs-lookup"><span data-stu-id="7038e-119">1</span></span>|<span data-ttu-id="7038e-120">Wyłącz możliwość przesłonięcia ustawień Fusion.</span><span class="sxs-lookup"><span data-stu-id="7038e-120">Disable the ability to override Fusion settings.</span></span> <span data-ttu-id="7038e-121">Spowoduje to przywrócenie zachowania wcześniejszych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7038e-121">This reverts to the behavior of earlier versions of the .NET Framework.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7038e-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7038e-122">Child Elements</span></span>  
 <span data-ttu-id="7038e-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="7038e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7038e-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7038e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="7038e-125">Element</span><span class="sxs-lookup"><span data-stu-id="7038e-125">Element</span></span>|<span data-ttu-id="7038e-126">Opis</span><span class="sxs-lookup"><span data-stu-id="7038e-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="7038e-127">Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7038e-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="7038e-128">Zawiera informacje dotyczące powiązania zestawu oraz wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="7038e-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7038e-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7038e-129">Remarks</span></span>  
 <span data-ttu-id="7038e-130">Począwszy od .NET Framework 4, domyślnym zachowaniem jest umożliwienie <xref:System.AppDomainManager> obiektowi przesłania ustawień konfiguracji przy użyciu <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości lub <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody <xref:System.AppDomainSetup> obiektu, który jest przesyłany do implementacji <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody w podklasy <xref:System.AppDomainManager> .</span><span class="sxs-lookup"><span data-stu-id="7038e-130">Starting with the .NET Framework 4, the default behavior is to allow the <xref:System.AppDomainManager> object to override configuration settings by using the <xref:System.AppDomainSetup.ConfigurationFile%2A> property or the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method of the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method, in your subclass of <xref:System.AppDomainManager>.</span></span> <span data-ttu-id="7038e-131">W przypadku domyślnej domeny aplikacji zmiany ustawień zastępują ustawienia, które zostały określone przez plik konfiguracyjny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7038e-131">For the default application domain, the settings you change override the settings that were specified by the application configuration file.</span></span> <span data-ttu-id="7038e-132">W przypadku innych domen aplikacji zastępują one ustawienia konfiguracji, które zostały przesłane do <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody lub.</span><span class="sxs-lookup"><span data-stu-id="7038e-132">For other application domains, they override the configuration settings that were passed to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7038e-133">Można przekazać nowe informacje konfiguracyjne lub przekazać wartość null ( `Nothing` w Visual Basic), aby wyeliminować przekazane informacje o konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7038e-133">You can either pass new configuration information, or pass null (`Nothing` in Visual Basic) to eliminate configuration information that was passed in.</span></span>  
  
 <span data-ttu-id="7038e-134">Nie przekazuj informacji o konfiguracji do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości i <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7038e-134">Do not pass configuration information to both the <xref:System.AppDomainSetup.ConfigurationFile%2A> property and the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method.</span></span> <span data-ttu-id="7038e-135">W przypadku przekazania informacji o konfiguracji do obu tych informacji przekazywane do <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości zostanie zignorowane, ponieważ <xref:System.AppDomainSetup.SetConfigurationBytes%2A> Metoda przesłania informacje o konfiguracji z pliku konfiguracyjnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7038e-135">If you pass configuration information to both, the information you pass to the <xref:System.AppDomainSetup.ConfigurationFile%2A> property is ignored, because the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method overrides configuration information from the application configuration file.</span></span> <span data-ttu-id="7038e-136">W przypadku użycia <xref:System.AppDomainSetup.ConfigurationFile%2A> właściwości można przekazać wartość null ( `Nothing` w Visual Basic) do <xref:System.AppDomainSetup.SetConfigurationBytes%2A> metody, aby wyeliminować wszystkie bajty konfiguracyjne, które zostały określone w wywołaniu <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> metody lub.</span><span class="sxs-lookup"><span data-stu-id="7038e-136">If you use the <xref:System.AppDomainSetup.ConfigurationFile%2A> property, you can pass null (`Nothing` in Visual Basic) to the <xref:System.AppDomainSetup.SetConfigurationBytes%2A> method to eliminate any configuration bytes that were specified in the call to the <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7038e-137">Oprócz informacji o konfiguracji można zmienić następujące ustawienia w <xref:System.AppDomainSetup> obiekcie, który jest przesyłany do implementacji metody:,,,,,,,,,, <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> <xref:System.AppDomainSetup.ApplicationBase%2A> <xref:System.AppDomainSetup.ApplicationName%2A> <xref:System.AppDomainSetup.CachePath%2A> <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A> <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> <xref:System.AppDomainSetup.DisallowCodeDownload%2A> <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.ShadowCopyDirectories%2A> , i <xref:System.AppDomainSetup.ShadowCopyFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="7038e-137">In addition to configuration information, you can change the following settings on the <xref:System.AppDomainSetup> object that is passed to your implementation of the <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> method: <xref:System.AppDomainSetup.ApplicationBase%2A>, <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>, <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A>, <xref:System.AppDomainSetup.DisallowCodeDownload%2A>, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, <xref:System.AppDomainSetup.DynamicBase%2A>, <xref:System.AppDomainSetup.LoaderOptimization%2A>, <xref:System.AppDomainSetup.PrivateBinPath%2A>, <xref:System.AppDomainSetup.PrivateBinPathProbe%2A>, <xref:System.AppDomainSetup.ShadowCopyDirectories%2A>, and <xref:System.AppDomainSetup.ShadowCopyFiles%2A>.</span></span>  
  
 <span data-ttu-id="7038e-138">Alternatywą wobec korzystania z `<disableFusionUpdatesFromADManager>` elementu jest wyłączenie domyślnego zachowania przez utworzenie ustawienia rejestru lub ustawienie zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="7038e-138">As an alternative to using the `<disableFusionUpdatesFromADManager>` element, you can disable the default behavior by creating a registry setting or by setting an environment variable.</span></span> <span data-ttu-id="7038e-139">W rejestrze utwórz wartość DWORD o nazwie `COMPLUS_disableFusionUpdatesFromADManager` w obszarze `HKCU\Software\Microsoft\.NETFramework` lub `HKLM\Software\Microsoft\.NETFramework` , a następnie ustaw wartość 1.</span><span class="sxs-lookup"><span data-stu-id="7038e-139">In the registry, create a DWORD value named `COMPLUS_disableFusionUpdatesFromADManager` under `HKCU\Software\Microsoft\.NETFramework` or `HKLM\Software\Microsoft\.NETFramework`, and set the value to 1.</span></span> <span data-ttu-id="7038e-140">W wierszu polecenia Ustaw wartość zmiennej środowiskowej `COMPLUS_disableFusionUpdatesFromADManager` na 1.</span><span class="sxs-lookup"><span data-stu-id="7038e-140">At the command line, set the environment variable `COMPLUS_disableFusionUpdatesFromADManager` to 1.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7038e-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="7038e-141">Example</span></span>  
 <span data-ttu-id="7038e-142">Poniższy przykład pokazuje, jak wyłączyć możliwość zastąpienia ustawień Fusion przy użyciu `<disableFusionUpdatesFromADManager>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7038e-142">The following example shows how to disable the ability to override Fusion settings by using the `<disableFusionUpdatesFromADManager>` element.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7038e-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7038e-143">See also</span></span>

- [<span data-ttu-id="7038e-144">Schemat ustawień środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="7038e-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7038e-145">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="7038e-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7038e-146">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7038e-146">How the Runtime Locates Assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
