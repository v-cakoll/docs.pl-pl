---
title: 'Ograniczenie: wersjonowanie produktu'
description: W tym artykule dowiesz się, jak .NET Framework 4,6 i nowsze wersje produktu zmieniły się z poprzednich wersji.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475401"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="b342b-103">Ograniczenie: wersjonowanie produktu</span><span class="sxs-lookup"><span data-stu-id="b342b-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="b342b-104">W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="b342b-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="b342b-105">Zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="b342b-105">Product versioning changes</span></span>

<span data-ttu-id="b342b-106">Poniżej przedstawiono szczegółowe zmiany:</span><span class="sxs-lookup"><span data-stu-id="b342b-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="b342b-107">Wartość `Version` wpisu w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu zmieniła się na `4.6.` *XXXXX* dla .NET Framework 4,6 i jego wydań punktów oraz do `4.7.` *XXXXX* dla .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="b342b-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="b342b-108">W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.` *XXXXX*.</span><span class="sxs-lookup"><span data-stu-id="b342b-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="b342b-109">Wersja plików i produktów dla plików .NET Framework zmieniła się ze schematu wcześniejszej wersji programu `4.0.30319.x` na `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a w `4.7.X.0` przypadku .NET Framework 4,7 i jego wydań punktów.</span><span class="sxs-lookup"><span data-stu-id="b342b-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="b342b-110">Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.</span><span class="sxs-lookup"><span data-stu-id="b342b-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="b342b-111"><xref:System.Reflection.AssemblyFileVersionAttribute>Atrybuty i <xref:System.Reflection.AssemblyInformationalVersionAttribute> dla zestawów zarządzanych mają <xref:System.Version> wartości w postaci `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów oraz `4.7.X.0` dla .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="b342b-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="b342b-112">Począwszy od .NET Framework 4,6, <xref:System.Environment.Version%2A?displayProperty=nameWithType> Właściwość zwraca ciąg stałej wersji `4.0.30319.42000` .</span><span class="sxs-lookup"><span data-stu-id="b342b-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="b342b-113">W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie, `4.0.30319.xxxxx` gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="b342b-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="b342b-114">Należy pamiętać, że kod aplikacji nie jest zalecany we <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b342b-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="b342b-115">Obsługa zmian wersji produktu</span><span class="sxs-lookup"><span data-stu-id="b342b-115">Handling the product versioning changes</span></span>

<span data-ttu-id="b342b-116">Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:</span><span class="sxs-lookup"><span data-stu-id="b342b-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="b342b-117">Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="b342b-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="b342b-118">Aby określić ścieżkę instalacji .NET Framework, użyj wartości `InstallPath` wpisu w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu.</span><span class="sxs-lookup"><span data-stu-id="b342b-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b342b-119">Nazwa podklucza to `NET Framework Setup` , nie `.NET Framework Setup` .</span><span class="sxs-lookup"><span data-stu-id="b342b-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="b342b-120">Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="b342b-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="b342b-121">Aby uzyskać wersję środowiska CLR, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="b342b-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="b342b-122">W przypadku .NET Framework 4 i jego wydań (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca ciąg `v4.0.30319` .</span><span class="sxs-lookup"><span data-stu-id="b342b-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="b342b-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b342b-123">See also</span></span>

- [<span data-ttu-id="b342b-124">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="b342b-124">Application compatibility</span></span>](application-compatibility.md)
