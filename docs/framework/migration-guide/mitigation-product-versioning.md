---
title: Środki zaradcze Przechowywanie wersji produktu
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91db9d8c6fccf75bc9025a9487517e8c55d016cc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779211"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="5fae5-102">Środki zaradcze Przechowywanie wersji produktu</span><span class="sxs-lookup"><span data-stu-id="5fae5-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="5fae5-103">W .NET Framework 4,6 i nowszych wersja produktu zmieniła się z poprzednich wersji .NET Framework (.NET Framework 4, 4,5, 4.5.1 i 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="5fae5-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="5fae5-104">Zmiany wersji produktu</span><span class="sxs-lookup"><span data-stu-id="5fae5-104">Product versioning changes</span></span>

<span data-ttu-id="5fae5-105">Poniżej przedstawiono szczegółowe zmiany:</span><span class="sxs-lookup"><span data-stu-id="5fae5-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="5fae5-106">Wartość `Version` wpisu `4.7.` `4.6.` w kluczu zmieniła się na XXXXX dla .NET Framework 4,6 i jego wydań punktów oraz do XXXXX dla .NET Framework 4,7. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`</span><span class="sxs-lookup"><span data-stu-id="5fae5-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="5fae5-107">W .NET Framework 4,5, 4.5.1 i 4.5.2 ma format `4.5.` *XXXXX*.</span><span class="sxs-lookup"><span data-stu-id="5fae5-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="5fae5-108">Wersja plików i produktów dla plików .NET Framework zmieniła się ze schematu wcześniejszej wersji programu `4.0.30319.x` na `4.6.X.0` dla .NET Framework 4,6 i jego wydań `4.7.X.0` punktów, a w przypadku .NET Framework 4,7 i jego wydań punktów.</span><span class="sxs-lookup"><span data-stu-id="5fae5-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="5fae5-109">Te nowe wartości są widoczne podczas przeglądania **Właściwości** pliku po kliknięciu prawym przyciskiem myszy pliku.</span><span class="sxs-lookup"><span data-stu-id="5fae5-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="5fae5-110"><xref:System.Version> `4.7.X.0` `4.6.X.0` Atrybuty i dla<xref:System.Reflection.AssemblyInformationalVersionAttribute> zestawów zarządzanych mają wartości w postaci dla .NET Framework 4,6 i jego wydań punktów oraz dla .NET Framework 4,7. <xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="5fae5-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="5fae5-111">Począwszy od .NET Framework 4,6, <xref:System.Environment.Version%2A?displayProperty=nameWithType> Właściwość zwraca ciąg `4.0.30319.42000`stałej wersji.</span><span class="sxs-lookup"><span data-stu-id="5fae5-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="5fae5-112">W .NET Framework 4, 4,5, 4.5.1 i 4.5.2 zwraca ciągi wersji w formacie `4.0.30319.xxxxx` , gdzie `xxxxx` jest mniejsza niż 42000 (na przykład "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="5fae5-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="5fae5-113">Należy pamiętać, że kod aplikacji nie jest zalecany we <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="5fae5-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="5fae5-114">Obsługa zmian wersji produktu</span><span class="sxs-lookup"><span data-stu-id="5fae5-114">Handling the product versioning changes</span></span>

<span data-ttu-id="5fae5-115">Ogólnie rzecz biorąc aplikacje powinny zależeć od zalecanych technik wykrywania takich elementów jak wersja środowiska uruchomieniowego .NET Framework i katalogu instalacyjnego:</span><span class="sxs-lookup"><span data-stu-id="5fae5-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="5fae5-116">Aby wykryć wersję środowiska uruchomieniowego .NET Framework, zobacz [How to: Ustal, które wersje .NET Framework są](how-to-determine-which-versions-are-installed.md)zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="5fae5-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="5fae5-117">Aby określić ścieżkę instalacji .NET Framework, użyj wartości `InstallPath` wpisu `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` w kluczu.</span><span class="sxs-lookup"><span data-stu-id="5fae5-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="5fae5-118">Nazwa podklucza `NET Framework Setup`to, `.NET Framework Setup`nie.</span><span class="sxs-lookup"><span data-stu-id="5fae5-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="5fae5-119">Aby określić ścieżkę katalogu do .NET Framework środowiska uruchomieniowego języka wspólnego, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="5fae5-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="5fae5-120">Aby uzyskać wersję środowiska CLR, wywołaj <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodę.</span><span class="sxs-lookup"><span data-stu-id="5fae5-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="5fae5-121">W przypadku .NET Framework 4 i jego wydań (.NET Framework 4,5, 4.5.1, 4.5.2 i .NET Framework 4,6, 4.6.1, 4.6.2 i 4,7) zwraca ciąg `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="5fae5-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fae5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5fae5-122">See also</span></span>

- [<span data-ttu-id="5fae5-123">Zmiany środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="5fae5-123">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
