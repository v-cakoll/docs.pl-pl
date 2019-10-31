---
title: 'Ograniczenie: wersjonowanie produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 63075136b7de4aeaa4f94c092996ae1829b449a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126157"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="4bafb-102">Ograniczenie: wersjonowanie produktu</span><span class="sxs-lookup"><span data-stu-id="4bafb-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="4bafb-103">W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="4bafb-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="4bafb-104">Zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="4bafb-104">Product versioning changes</span></span>

<span data-ttu-id="4bafb-105">Poniżej przedstawiono szczegółowe zmiany:</span><span class="sxs-lookup"><span data-stu-id="4bafb-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="4bafb-106">Wartość wpisu `Version` w kluczu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` została zmieniona na `4.6.`*XXXXX* dla .NET Framework 4,6 i jego wydań punktów oraz `4.7.`*xxxxx* dla .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="4bafb-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="4bafb-107">W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.`*XXXXX*.</span><span class="sxs-lookup"><span data-stu-id="4bafb-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="4bafb-108">Wersje plików i produktów dla plików .NET Framework zmieniły się ze schematu wcześniejszej wersji `4.0.30319.x` do `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a `4.7.X.0` .NET Framework 4,7 i jego wydania punktów.</span><span class="sxs-lookup"><span data-stu-id="4bafb-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="4bafb-109">Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.</span><span class="sxs-lookup"><span data-stu-id="4bafb-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="4bafb-110">Atrybuty <xref:System.Reflection.AssemblyFileVersionAttribute> i <xref:System.Reflection.AssemblyInformationalVersionAttribute> dla zestawów zarządzanych mają <xref:System.Version> wartości w postaci `4.6.X.0` dla .NET Framework 4,6 i jego wydań punktów, a `4.7.X.0` .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="4bafb-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="4bafb-111">Począwszy od .NET Framework 4,6, właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> zwraca ciąg stałej wersji `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="4bafb-112">W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie `4.0.30319.xxxxx` gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="4bafb-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="4bafb-113">Należy pamiętać, że kod aplikacji nie jest zalecany we właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="4bafb-114">Obsługa zmian wersji produktu</span><span class="sxs-lookup"><span data-stu-id="4bafb-114">Handling the product versioning changes</span></span>

<span data-ttu-id="4bafb-115">Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:</span><span class="sxs-lookup"><span data-stu-id="4bafb-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="4bafb-116">Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Określanie, które wersje .NET Framework są zainstalowane](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="4bafb-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="4bafb-117">Aby określić ścieżkę instalacji .NET Framework, użyj wartości wpisu `InstallPath` w kluczu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="4bafb-118">Nazwa podklucza jest `NET Framework Setup`, a nie `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="4bafb-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="4bafb-119">Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj metodę <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="4bafb-120">Aby uzyskać wersję środowiska CLR, wywołaj metodę <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4bafb-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="4bafb-121">W przypadku .NET Framework 4 i jego wydań punktów (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca `v4.0.30319`ciąg.</span><span class="sxs-lookup"><span data-stu-id="4bafb-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="4bafb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4bafb-122">See also</span></span>

- [<span data-ttu-id="4bafb-123">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="4bafb-123">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
