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
ms.openlocfilehash: fe003a6c74da59c1cb47a0f12a8597143916e320
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138639"
---
# <a name="set-assembly-attributes"></a><span data-ttu-id="2bad2-102">Ustawianie atrybutów zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-102">Set assembly attributes</span></span>

<span data-ttu-id="2bad2-103">Atrybuty zestawu są wartościami, które zawierają informacje o zestawie.</span><span class="sxs-lookup"><span data-stu-id="2bad2-103">Assembly attributes are values that provide information about an assembly.</span></span> <span data-ttu-id="2bad2-104">Atrybuty są podzielone na następujące zestawy informacji:</span><span class="sxs-lookup"><span data-stu-id="2bad2-104">The attributes are divided into the following sets of information:</span></span>

- <span data-ttu-id="2bad2-105">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-105">Assembly identity attributes</span></span>

- <span data-ttu-id="2bad2-106">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="2bad2-106">Informational attributes</span></span>

- <span data-ttu-id="2bad2-107">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-107">Assembly manifest attributes</span></span>

- <span data-ttu-id="2bad2-108">Atrybuty silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="2bad2-108">Strong name attributes</span></span>

## <a name="assembly-identity-attributes"></a><span data-ttu-id="2bad2-109">Atrybuty tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-109">Assembly identity attributes</span></span>

<span data-ttu-id="2bad2-110">Trzy atrybuty wraz z silną nazwą (jeśli dotyczy) określają tożsamość zestawu: nazwę, wersję i kulturę.</span><span class="sxs-lookup"><span data-stu-id="2bad2-110">Three attributes, together with a strong name (if applicable), determine the identity of an assembly: name, version, and culture.</span></span> <span data-ttu-id="2bad2-111">Te atrybuty tworzą pełną nazwę zestawu i są wymagane podczas odwoływania się do zestawu w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2bad2-111">These attributes form the full name of the assembly and are required when referencing the assembly in code.</span></span> <span data-ttu-id="2bad2-112">Można użyć atrybutów, aby ustawić wersję i kulturę zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-112">You can use attributes to set an assembly's version and culture.</span></span> <span data-ttu-id="2bad2-113">Kompilator lub [konsolidator zestawu (Al. exe)](../../framework/tools/al-exe-assembly-linker.md) ustawia wartość nazwy podczas tworzenia zestawu, na podstawie pliku zawierającego manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-113">The compiler or the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) sets the name value when the assembly is created, based on the file containing the assembly manifest.</span></span>

<span data-ttu-id="2bad2-114">W poniższej tabeli opisano atrybuty wersji i kultury.</span><span class="sxs-lookup"><span data-stu-id="2bad2-114">The following table describes the version and culture attributes.</span></span>

|<span data-ttu-id="2bad2-115">Atrybut tożsamości zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-115">Assembly identity attribute</span></span>|<span data-ttu-id="2bad2-116">Opis</span><span class="sxs-lookup"><span data-stu-id="2bad2-116">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|<span data-ttu-id="2bad2-117">Pole wyliczane wskazujące kulturę obsługiwaną przez zestaw.</span><span class="sxs-lookup"><span data-stu-id="2bad2-117">Enumerated field indicating the culture that the assembly supports.</span></span> <span data-ttu-id="2bad2-118">Zestaw może również określać niezależność kultury, wskazując, że zawiera zasoby dla kultury domyślnej.</span><span class="sxs-lookup"><span data-stu-id="2bad2-118">An assembly can also specify culture independence, indicating that it contains the resources for the default culture.</span></span> <span data-ttu-id="2bad2-119">**Uwaga:**  Środowisko uruchomieniowe traktuje dowolny zestaw, który nie ma atrybutu kultury ustawionego na wartość null jako zestaw satelicki.</span><span class="sxs-lookup"><span data-stu-id="2bad2-119">**Note:**  The runtime treats any assembly that does not have the culture attribute set to null as a satellite assembly.</span></span> <span data-ttu-id="2bad2-120">Takie zestawy podlegają regułom powiązania zestawu satelickiego.</span><span class="sxs-lookup"><span data-stu-id="2bad2-120">Such assemblies are subject to satellite assembly binding rules.</span></span> <span data-ttu-id="2bad2-121">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2bad2-121">For more information, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>|
|<xref:System.Reflection.AssemblyFlagsAttribute>|<span data-ttu-id="2bad2-122">Wartość, która ustawia atrybuty zestawu, na przykład czy zestaw może być uruchamiany obok siebie.</span><span class="sxs-lookup"><span data-stu-id="2bad2-122">Value that sets assembly attributes, such as whether the assembly can be run side by side.</span></span>|
|<xref:System.Reflection.AssemblyVersionAttribute>|<span data-ttu-id="2bad2-123">Wartość liczbowa w formacie *głównym*. *pomocnicze*. *kompilacja*. *poprawka* (na przykład 2.4.0.0).</span><span class="sxs-lookup"><span data-stu-id="2bad2-123">Numeric value in the format *major*.*minor*.*build*.*revision* (for example, 2.4.0.0).</span></span> <span data-ttu-id="2bad2-124">Środowisko uruchomieniowe języka wspólnego używa tej wartości do wykonywania operacji powiązań w zestawach o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="2bad2-124">The common language runtime uses this value to perform binding operations in strong-named assemblies.</span></span> <span data-ttu-id="2bad2-125">**Uwaga:**  Jeśli atrybut <xref:System.Reflection.AssemblyInformationalVersionAttribute> nie jest stosowany do zestawu, numer wersji określony przez atrybut <xref:System.Reflection.AssemblyVersionAttribute> jest używany przez właściwości <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bad2-125">**Note:**  If the <xref:System.Reflection.AssemblyInformationalVersionAttribute> attribute is not applied to an assembly, the version number specified by the <xref:System.Reflection.AssemblyVersionAttribute> attribute is used by the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>, <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>, and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|

<span data-ttu-id="2bad2-126">Poniższy przykład kodu pokazuje, jak zastosować wersję i atrybuty kultury do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-126">The following code example shows how to apply the version and culture attributes to an assembly.</span></span>

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

## <a name="informational-attributes"></a><span data-ttu-id="2bad2-127">Atrybuty informacyjne</span><span class="sxs-lookup"><span data-stu-id="2bad2-127">Informational attributes</span></span>

<span data-ttu-id="2bad2-128">Można użyć atrybutów informacyjnych w celu podania dodatkowych informacji o firmie lub produkcie dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-128">You can use informational attributes to provide additional company or product information for an assembly.</span></span> <span data-ttu-id="2bad2-129">W poniższej tabeli opisano atrybuty informacyjne, które można zastosować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-129">The following table describes the informational attributes you can apply to an assembly.</span></span>

|<span data-ttu-id="2bad2-130">Atrybut informacyjny</span><span class="sxs-lookup"><span data-stu-id="2bad2-130">Informational attribute</span></span>|<span data-ttu-id="2bad2-131">Opis</span><span class="sxs-lookup"><span data-stu-id="2bad2-131">Description</span></span>|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|<span data-ttu-id="2bad2-132">Wartość ciągu określająca nazwę firmy.</span><span class="sxs-lookup"><span data-stu-id="2bad2-132">String value specifying a company name.</span></span>|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|<span data-ttu-id="2bad2-133">Wartość ciągu określająca informacje o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="2bad2-133">String value specifying copyright information.</span></span>|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|<span data-ttu-id="2bad2-134">Wartość ciągu określająca numer wersji pliku Win32.</span><span class="sxs-lookup"><span data-stu-id="2bad2-134">String value specifying the Win32 file version number.</span></span> <span data-ttu-id="2bad2-135">Zwykle jest to domyślna wersja zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-135">This normally defaults to the assembly version.</span></span>|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|<span data-ttu-id="2bad2-136">Wartość ciągu określająca informacje o wersji, które nie są używane przez środowisko uruchomieniowe języka wspólnego, takie jak pełny numer wersji produktu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-136">String value specifying version information that is not used by the common language runtime, such as a full product version number.</span></span> <span data-ttu-id="2bad2-137">**Uwaga:**  Jeśli ten atrybut jest stosowany do zestawu, ciąg, który określa, można uzyskać w czasie wykonywania przy użyciu właściwości <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2bad2-137">**Note:**  If this attribute is applied to an assembly, the string it specifies can be obtained at run time by using the <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="2bad2-138">Ten ciąg jest również używany w ścieżce i klucz rejestru podany przez <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2bad2-138">The string is also used in the path and registry key provided by the <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> properties.</span></span>|
|<xref:System.Reflection.AssemblyProductAttribute>|<span data-ttu-id="2bad2-139">Wartość ciągu określająca informacje o produkcie.</span><span class="sxs-lookup"><span data-stu-id="2bad2-139">String value specifying product information.</span></span>|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|<span data-ttu-id="2bad2-140">Wartość ciągu określająca informacje o znakach towarowych.</span><span class="sxs-lookup"><span data-stu-id="2bad2-140">String value specifying trademark information.</span></span>|

<span data-ttu-id="2bad2-141">Te atrybuty mogą być wyświetlane na stronie właściwości systemu Windows zestawu lub można je zastąpić przy użyciu opcji kompilatora **/win32res** , aby określić własny plik zasobów Win32.</span><span class="sxs-lookup"><span data-stu-id="2bad2-141">These attributes can appear on the Windows Properties page of the assembly, or they can be overridden using the **/win32res** compiler option to specify your own Win32 resource file.</span></span>

## <a name="assembly-manifest-attributes"></a><span data-ttu-id="2bad2-142">Atrybuty manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-142">Assembly manifest attributes</span></span>

<span data-ttu-id="2bad2-143">Można użyć atrybutów manifestu zestawu, aby podać informacje w manifeście zestawu, w tym tytuł, opis, alias domyślny i konfigurację.</span><span class="sxs-lookup"><span data-stu-id="2bad2-143">You can use assembly manifest attributes to provide information in the assembly manifest, including title, description, the default alias, and configuration.</span></span> <span data-ttu-id="2bad2-144">W poniższej tabeli opisano atrybuty manifestu zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-144">The following table describes the assembly manifest attributes.</span></span>

|<span data-ttu-id="2bad2-145">Atrybut manifestu zestawu</span><span class="sxs-lookup"><span data-stu-id="2bad2-145">Assembly manifest attribute</span></span>|<span data-ttu-id="2bad2-146">Opis</span><span class="sxs-lookup"><span data-stu-id="2bad2-146">Description</span></span>|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|<span data-ttu-id="2bad2-147">Wartość ciągu określająca konfigurację zestawu, na przykład detaliczną lub debug.</span><span class="sxs-lookup"><span data-stu-id="2bad2-147">String value indicating the configuration of the assembly, such as Retail or Debug.</span></span> <span data-ttu-id="2bad2-148">Środowisko uruchomieniowe nie używa tej wartości.</span><span class="sxs-lookup"><span data-stu-id="2bad2-148">The runtime does not use this value.</span></span>|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|<span data-ttu-id="2bad2-149">Wartość ciągu określająca domyślny alias, który będzie używany przez odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="2bad2-149">String value specifying a default alias to be used by referencing assemblies.</span></span> <span data-ttu-id="2bad2-150">Ta wartość zapewnia przyjazną nazwę, gdy nazwa samego zestawu nie jest przyjazna (na przykład wartość identyfikatora GUID).</span><span class="sxs-lookup"><span data-stu-id="2bad2-150">This value provides a friendly name when the name of the assembly itself is not friendly (such as a GUID value).</span></span> <span data-ttu-id="2bad2-151">Ta wartość może być również używana jako krótka forma pełnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-151">This value can also be used as a short form of the full assembly name.</span></span>|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|<span data-ttu-id="2bad2-152">Wartość ciągu określająca Krótki opis, który podsumowuje charakter i cel zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-152">String value specifying a short description that summarizes the nature and purpose of the assembly.</span></span>|
|<xref:System.Reflection.AssemblyTitleAttribute>|<span data-ttu-id="2bad2-153">Wartość ciągu określająca przyjazną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-153">String value specifying a friendly name for the assembly.</span></span> <span data-ttu-id="2bad2-154">Na przykład zestaw o nazwie *comdlg* może mieć tytuł Microsoft Common Dialogs Control.</span><span class="sxs-lookup"><span data-stu-id="2bad2-154">For example, an assembly named *comdlg* might have the title Microsoft Common Dialog Control.</span></span>|

## <a name="strong-name-attributes"></a><span data-ttu-id="2bad2-155">Atrybuty silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="2bad2-155">Strong name attributes</span></span>

<span data-ttu-id="2bad2-156">Aby ustawić silną nazwę zestawu, można użyć atrybutów silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2bad2-156">You can use strong name attributes to set a strong name for an assembly.</span></span> <span data-ttu-id="2bad2-157">W poniższej tabeli opisano atrybuty silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="2bad2-157">The following table describes the strong name attributes.</span></span>

|<span data-ttu-id="2bad2-158">Atrybut silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="2bad2-158">Strong name attribute</span></span>|<span data-ttu-id="2bad2-159">Opis</span><span class="sxs-lookup"><span data-stu-id="2bad2-159">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|<span data-ttu-id="2bad2-160">Wartość logiczna wskazująca, że jest używane podpisywanie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="2bad2-160">Boolean value indicating that delay signing is being used.</span></span>|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|<span data-ttu-id="2bad2-161">Wartość ciągu wskazująca nazwę pliku, który zawiera klucz publiczny (w przypadku korzystania z opóźnienia podpisywania) lub klucze publiczny i prywatny przekazanie jako parametr do konstruktora tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-161">String value indicating the name of the file that contains either the public key (if using delay signing) or both the public and private keys passed as a parameter to the constructor of this attribute.</span></span> <span data-ttu-id="2bad2-162">Należy pamiętać, że nazwa pliku jest względna w stosunku do ścieżki pliku wyjściowego ( *. exe* lub *. dll*), a nie ścieżki pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="2bad2-162">Note that the file name is relative to the output file path (the *.exe* or *.dll*), not the source file path.</span></span>|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|<span data-ttu-id="2bad2-163">Wskazuje kontener kluczy, który zawiera parę kluczy przekazaną jako parametr do konstruktora tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2bad2-163">Indicates the key container that contains the key pair passed as a parameter to the constructor of this attribute.</span></span>|

<span data-ttu-id="2bad2-164">Poniższy przykład kodu pokazuje atrybuty do zastosowania podczas korzystania z opóźnienia podpisywania w celu utworzenia zestawu o silnej nazwie z plikiem klucza publicznego o nazwie *klucze. snk*.</span><span class="sxs-lookup"><span data-stu-id="2bad2-164">The following code example shows the attributes to apply when using delay signing to create a strong-named assembly with a public key file called *myKey.snk*.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2bad2-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bad2-165">See also</span></span>

- [<span data-ttu-id="2bad2-166">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="2bad2-166">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="2bad2-167">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="2bad2-167">Program with assemblies</span></span>](program.md)
