---
title: Ustawianie atrybutów zestawu
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 0e4e2e595ed4f95511bd23ab0ed00139f71b2c8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73740475"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="60d98-102">Ustawianie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-102">Set assembly attributes</span></span>

<span data-ttu-id="60d98-103">Atrybuty zestawu są wartościami, które dostarczają informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="60d98-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="60d98-104">Atrybuty są podzielone na następujące zestawy informacji:</span><span class="sxs-lookup"><span data-stu-id="60d98-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="60d98-105">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-105">Assembly identity attributes</span></span>

- <span data-ttu-id="60d98-106">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="60d98-106">Informational attributes</span></span>

- <span data-ttu-id="60d98-107">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="60d98-108">Atrybuty silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="60d98-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="60d98-109">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-109">Assembly identity attributes</span></span>

<span data-ttu-id="60d98-110">Trzy atrybuty, wraz z silną nazwą (jeśli dotyczy), określają tożsamość zestawu: nazwa, wersja i kultura.</span><span class="sxs-lookup"><span data-stu-id="60d98-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="60d98-111">Atrybuty te tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do zestawu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="60d98-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="60d98-112">Atrybuty służy do ustawiania wersji zestawu i kultury.</span><span class="sxs-lookup"><span data-stu-id="60d98-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="60d98-113">Kompilator lub [konsolidator zestawu (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy podczas tworzenia zestawu, na podstawie pliku zawierającego manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="60d98-114">W poniższej tabeli opisano atrybuty wersji i kultury.</span><span class="sxs-lookup"><span data-stu-id="60d98-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="60d98-115">Atrybut tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-115">Assembly identity attribute</span></span>|<span data-ttu-id="60d98-116">Opis</span><span class="sxs-lookup"><span data-stu-id="60d98-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="60d98-117">Pole wyliczone wskazujące kulturę, która obsługuje zestaw.</span><span class="sxs-lookup"><span data-stu-id="60d98-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="60d98-118">Zestaw można również określić niezależność kultury, wskazując, że zawiera zasoby dla kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="60d98-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="60d98-119">**Uwaga:**  Czas wykonywania traktuje każdy zestaw, który nie ma atrybutkultury ustawiony na null jako zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="60d98-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="60d98-120">Takie zestawy podlegają regułom wiązania zestawu satelitarnego.</span><span class="sxs-lookup"><span data-stu-id="60d98-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="60d98-121">Aby uzyskać więcej informacji, zobacz [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="60d98-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="60d98-122">Wartość, która ustawia atrybuty złożenia, takie jak czy zestaw może być uruchamiany obok siebie.</span><span class="sxs-lookup"><span data-stu-id="60d98-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="60d98-123">Wartość liczbowa w formacie *głównym*. *drobne*. *budować*. *(na* przykład 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="60d98-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="60d98-124">Czas wykonywania języka wspólnego używa tej wartości do wykonywania operacji wiązania w zestawach o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="60d98-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="60d98-125">**Uwaga:**  Jeśli <xref:System.Reflection.AssemblyInformationalVersionAttribute> atrybut nie jest stosowany do złożenia, numer wersji <xref:System.Reflection.AssemblyVersionAttribute> określony przez <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>atrybut <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>jest <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> używany przez , , i właściwości.</span><span class="sxs-lookup"><span data-stu-id="60d98-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="60d98-126">W poniższym przykładzie kodu pokazano, jak zastosować atrybuty wersji i kultury do zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a><span data-ttu-id="60d98-127">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="60d98-127">Informational attributes</span></span>

<span data-ttu-id="60d98-128">Atrybutów informacyjnych można użyć do podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="60d98-129">W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="60d98-130">Atrybut informacyjny</span><span class="sxs-lookup"><span data-stu-id="60d98-130">Informational attribute</span></span>|<span data-ttu-id="60d98-131">Opis</span><span class="sxs-lookup"><span data-stu-id="60d98-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="60d98-132">Wartość ciągu określająca nazwę firmy.</span><span class="sxs-lookup"><span data-stu-id="60d98-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="60d98-133">Wartość ciągu określająca informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="60d98-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="60d98-134">Wartość ciągu określająca numer wersji pliku Win32.</span><span class="sxs-lookup"><span data-stu-id="60d98-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="60d98-135">Jest to zwykle domyślnie do wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="60d98-136">Wartość ciągu określająca informacje o wersji, które nie są używane przez czas wykonywania języka wspólnego, takie jak pełny numer wersji produktu.</span><span class="sxs-lookup"><span data-stu-id="60d98-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="60d98-137">**Uwaga:**  Jeśli ten atrybut jest stosowany do zestawu, ciąg określa można uzyskać w <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> czasie wykonywania przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="60d98-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="60d98-138">Ciąg jest również używany w ścieżce i <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> kluczrejestru dostarczonych przez i właściwości.</span><span class="sxs-lookup"><span data-stu-id="60d98-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="60d98-139">Wartość ciągu określająca informacje o produkcie.</span><span class="sxs-lookup"><span data-stu-id="60d98-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="60d98-140">Wartość ciągu określająca informacje o znaku towarowym.</span><span class="sxs-lookup"><span data-stu-id="60d98-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="60d98-141">Te atrybuty mogą być wyświetlane na stronie Właściwości systemu Windows zestawu lub mogą być zastąpione przy użyciu opcji kompilatora **/win32res,** aby określić własny plik zasobu Win32.</span><span class="sxs-lookup"><span data-stu-id="60d98-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="60d98-142">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-142">Assembly manifest attributes</span></span>

<span data-ttu-id="60d98-143">Atrybutów manifestu zestawu można użyć do dostarczenia informacji w manifeście zestawu, w tym tytułu, opisu, domyślnego aliasu i konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="60d98-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="60d98-144">W poniższej tabeli opisano atrybuty manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="60d98-145">Atrybut manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="60d98-145">Assembly manifest attribute</span></span>|<span data-ttu-id="60d98-146">Opis</span><span class="sxs-lookup"><span data-stu-id="60d98-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="60d98-147">Wartość ciągu wskazująca konfigurację zestawu, na przykład Retail lub Debug.</span><span class="sxs-lookup"><span data-stu-id="60d98-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="60d98-148">Program runtime nie używa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="60d98-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="60d98-149">Wartość ciągu określająca alias domyślny, który ma być używany przez odwoływanie się do zestawów.</span><span class="sxs-lookup"><span data-stu-id="60d98-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="60d98-150">Ta wartość zapewnia przyjazną nazwę, gdy nazwa samego zestawu nie jest przyjazny (na przykład wartość guid).</span><span class="sxs-lookup"><span data-stu-id="60d98-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="60d98-151">Ta wartość może być również używana jako krótka forma pełnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="60d98-152">Wartość ciągu określająca krótki opis, który podsumowuje charakter i cel zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="60d98-153">Wartość ciągu określająca przyjazną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="60d98-154">Na przykład zestaw o nazwie *comdlg* może mieć tytuł Microsoft Common Dialog Control.</span><span class="sxs-lookup"><span data-stu-id="60d98-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="60d98-155">Atrybuty silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="60d98-155">Strong name attributes</span></span>

<span data-ttu-id="60d98-156">Atrybuty silnej nazwy można użyć, aby ustawić silną nazwę dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="60d98-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="60d98-157">W poniższej tabeli opisano atrybuty silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="60d98-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="60d98-158">Atrybut silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="60d98-158">Strong name attribute</span></span>|<span data-ttu-id="60d98-159">Opis</span><span class="sxs-lookup"><span data-stu-id="60d98-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="60d98-160">Wartość logiczna wskazująca, że używane jest podpisywanie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="60d98-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="60d98-161">Wartość ciągu wskazująca nazwę pliku, który zawiera klucz publiczny (jeśli używasz podpisywania opóźnienia) lub klucze publiczne i prywatne przekazywane jako parametr do konstruktora tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="60d98-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="60d98-162">Należy zauważyć, że nazwa pliku jest względem ścieżki pliku wyjściowego *(exe* lub *.dll),* a nie ścieżki pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="60d98-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="60d98-163">Wskazuje kontener kluczy, który zawiera parę kluczy przekazany jako parametr do konstruktora tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="60d98-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="60d98-164">Poniższy przykład kodu pokazuje atrybuty, które należy zastosować podczas podpisywania opóźnienia w celu utworzenia zestawu o silnej nazwie z plikiem klucza publicznego o nazwie *myKey.snk*.</span><span class="sxs-lookup"><span data-stu-id="60d98-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a><span data-ttu-id="60d98-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60d98-165">See also</span></span>

- [<span data-ttu-id="60d98-166">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="60d98-166">Create assemblies</span></span>](create.md)
