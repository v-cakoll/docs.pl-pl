---
title: 'Ograniczenie: wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457823"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="e8764-102">Ograniczenie: wersjonowanie produktu</span><span class="sxs-lookup"><span data-stu-id="e8764-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="e8764-103">W .NET Framework 4.6 i nowszych wersjach produktu została zmieniona z poprzednich wersji programu .NET Framework (.NET Framework 4, 4.5, 4.5.1 i 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="e8764-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="e8764-104">Zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="e8764-104">Product versioning changes</span></span>

<span data-ttu-id="e8764-105">Poniżej przedstawiono szczegółowe zmiany:</span><span class="sxs-lookup"><span data-stu-id="e8764-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="e8764-106">Wartość wpisu `Version` w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` kluczu została `4.6.`zmieniona na *xxxxx* dla .NET Framework 4.6 i jego wydania punktowe oraz `4.7.` *xxxxx* dla .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="e8764-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="e8764-107">W .NET Framework 4.5, 4.5.1 i 4.5.2 `4.5.`miał format *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="e8764-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="e8764-108">Przechowywanie wersji plików i produktów dla plików .NET Framework zostało `4.0.30319.x` `4.6.X.0` zmienione z wcześniejszego schematu przechowywania wersji na program `4.7.X.0` .NET Framework 4.6 i jego wersje punktowe oraz na platformie .NET Framework 4.7 i jego wydaniach punktowych.</span><span class="sxs-lookup"><span data-stu-id="e8764-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="e8764-109">Te nowe wartości można zobaczyć podczas wyświetlania **właściwości** pliku po kliknięciu prawym przyciskiem myszy na pliku.</span><span class="sxs-lookup"><span data-stu-id="e8764-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="e8764-110"><xref:System.Reflection.AssemblyFileVersionAttribute> Atrybuty <xref:System.Reflection.AssemblyInformationalVersionAttribute> i dla zestawów zarządzanych mają <xref:System.Version> wartości w formularzu `4.6.X.0` dla programu .NET `4.7.X.0` Framework 4.6 i jego wersji punktowych oraz dla programu .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="e8764-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="e8764-111">Począwszy od programu .NET Framework <xref:System.Environment.Version%2A?displayProperty=nameWithType> 4.6, `4.0.30319.42000`właściwość zwraca ciąg wersji stałej .</span><span class="sxs-lookup"><span data-stu-id="e8764-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="e8764-112">W .NET Framework 4, 4.5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie, `4.0.30319.xxxxx` w którym `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="e8764-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="e8764-113">Należy zauważyć, że nie zaleca się kod <xref:System.Environment.Version%2A?displayProperty=nameWithType> aplikacji przy żadnej nowej zależności od właściwości.</span><span class="sxs-lookup"><span data-stu-id="e8764-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="e8764-114">Obsługa zmian wersji produktu</span><span class="sxs-lookup"><span data-stu-id="e8764-114">Handling the product versioning changes</span></span>

<span data-ttu-id="e8764-115">Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich rzeczy, jak wersja środowiska wykonawczego programu .NET Framework i katalog instalacyjny:</span><span class="sxs-lookup"><span data-stu-id="e8764-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="e8764-116">Aby wykryć wersję środowiska uruchomieniowego programu .NET Framework, zobacz [Jak: Określanie zainstalowanych wersji programu .NET Framework](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="e8764-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="e8764-117">Aby określić ścieżkę instalacji dla programu .NET Framework, należy użyć wartości wpisu `InstallPath` w kluczu. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`</span><span class="sxs-lookup"><span data-stu-id="e8764-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="e8764-118">Nazwa podklucza `NET Framework Setup` `.NET Framework Setup`to , nie .</span><span class="sxs-lookup"><span data-stu-id="e8764-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="e8764-119">Aby określić ścieżkę katalogu do środowiska uruchomieniowego <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> języka wspólnego programu .NET Framework, należy wywołać metodę.</span><span class="sxs-lookup"><span data-stu-id="e8764-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="e8764-120">Aby uzyskać wersję CLR, <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> wywołaj metodę.</span><span class="sxs-lookup"><span data-stu-id="e8764-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="e8764-121">W przypadku programu .NET Framework 4 i jego wersji punktowych (.NET Framework 4.5, 4.5.1, 4.5.2 i .NET Framework 4.6, 4.6.1, `v4.0.30319`4.6.2 i 4.7) zwraca ciąg .</span><span class="sxs-lookup"><span data-stu-id="e8764-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8764-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8764-122">See also</span></span>

- [<span data-ttu-id="e8764-123">Zgodność aplikacji</span><span class="sxs-lookup"><span data-stu-id="e8764-123">Application compatibility</span></span>](application-compatibility.md)
