---
title: -sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53362c2eb5517d9230ea88975745315d6db7f1ba
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-sdkpath"></a><span data-ttu-id="d1e18-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="d1e18-102">-sdkpath</span></span>
<span data-ttu-id="d1e18-103">Określa lokalizację pliku mscorlib.dll i pliku Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="d1e18-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d1e18-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="d1e18-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d1e18-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="d1e18-106">Katalog zawierający wersji biblioteki mscorlib.dll i pliku Microsoft.VisualBasic.dll do użycia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d1e18-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="d1e18-107">Ta ścieżka nie została zweryfikowana, dopóki nie został załadowany.</span><span class="sxs-lookup"><span data-stu-id="d1e18-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="d1e18-108">Nazwę katalogu należy ująć w cudzysłów ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="d1e18-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1e18-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1e18-109">Remarks</span></span>  
 <span data-ttu-id="d1e18-110">Ta opcja nakazuje [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora, aby załadować mscorlib.dll i pliku Microsoft.VisualBasic.dll plików z lokalizacji innych niż domyślne.</span><span class="sxs-lookup"><span data-stu-id="d1e18-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="d1e18-111">`-sdkpath` Opcja został zaprojektowany do użytku z [- netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="d1e18-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="d1e18-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Używa różne wersje tych obsługuje bibliotek, aby uniknąć użycia typy i funkcje językowe nie znajdujące się na urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="d1e18-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1e18-113">`-sdkpath` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d1e18-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="d1e18-114">`-sdkpath` Opcja jest ustawiona, gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] urządzenia projektu jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="d1e18-114">The `-sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="d1e18-115">Można określić, czy kompilator powinien skompilować bez odwołania do Visual Basic Runtime Library przy użyciu `-vbruntime` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d1e18-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="d1e18-116">Aby uzyskać więcej informacji, zobacz [- vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="d1e18-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1e18-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1e18-117">Example</span></span>  
 <span data-ttu-id="d1e18-118">Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki Mscorlib.dll i pliku Microsoft.VisualBasic.dll znajdujące się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C.</span><span class="sxs-lookup"><span data-stu-id="d1e18-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="d1e18-119">Zazwyczaj należy użyć najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1e18-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1e18-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1e18-120">See Also</span></span>  
 [<span data-ttu-id="d1e18-121">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d1e18-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d1e18-122">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d1e18-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d1e18-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="d1e18-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="d1e18-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="d1e18-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
