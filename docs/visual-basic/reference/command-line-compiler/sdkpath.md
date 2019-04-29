---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
ms.openlocfilehash: 2024ccadb06fdea0c24d9d304c2fe040f8cce1d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639067"
---
# <a name="-sdkpath"></a><span data-ttu-id="17e72-102">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="17e72-102">-sdkpath</span></span>
<span data-ttu-id="17e72-103">Określa lokalizację mscorlib.dll i Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="17e72-103">Specifies the location of mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="17e72-104">Syntax</span></span>  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="17e72-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="17e72-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="17e72-106">Katalog zawierający wersji biblioteki mscorlib.dll i Microsoft.VisualBasic.dll na potrzeby kompilacji.</span><span class="sxs-lookup"><span data-stu-id="17e72-106">The directory containing the versions of mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="17e72-107">Ta ścieżka nie została zweryfikowana, dopóki nie jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="17e72-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="17e72-108">Nazwę katalogu należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="17e72-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17e72-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="17e72-109">Remarks</span></span>  
 <span data-ttu-id="17e72-110">Ta opcja nakazuje kompilatorowi języka Visual Basic obciążenia mscorlib.dll i Microsoft.VisualBasic.dll pliki z lokalizacji innych niż domyślne.</span><span class="sxs-lookup"><span data-stu-id="17e72-110">This option tells the Visual Basic compiler to load the mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="17e72-111">`-sdkpath` Opcja została zaprojektowana do użycia z [- netcf —](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="17e72-111">The `-sdkpath` option was designed to be used with [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="17e72-112">[!INCLUDE[Compact](~/includes/compact-md.md)] Używa różnych wersji tych Obsługa bibliotek, aby uniknąć użycia typów i funkcji języka, które nie znajdują się na urządzeniach.</span><span class="sxs-lookup"><span data-stu-id="17e72-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17e72-113">`-sdkpath` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="17e72-113">The `-sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="17e72-114">`-sdkpath` Ustawiono opcję po załadowaniu projektu urządzenia języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="17e72-114">The `-sdkpath` option is set when a Visual Basic device project is loaded.</span></span>  
  
 <span data-ttu-id="17e72-115">Można określić, czy kompilator powinien kompilować bez odwołania do biblioteki środowiska uruchomieniowego Visual Basic przy użyciu `-vbruntime` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="17e72-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `-vbruntime` compiler option.</span></span> <span data-ttu-id="17e72-116">Aby uzyskać więcej informacji, zobacz [- vbruntime —](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="17e72-116">For more information, see [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="17e72-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="17e72-117">Example</span></span>  
 <span data-ttu-id="17e72-118">Poniższy kod kompiluje `Myfile.vb` z [!INCLUDE[Compact](~/includes/compact-md.md)], przy użyciu wersji biblioteki Mscorlib.dll i Microsoft.VisualBasic.dll znajduje się w katalogu instalacji domyślnej z [!INCLUDE[Compact](~/includes/compact-md.md)] na dysku C.</span><span class="sxs-lookup"><span data-stu-id="17e72-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="17e72-119">Zazwyczaj używasz najnowszej wersji [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="17e72-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="17e72-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17e72-120">See also</span></span>

- [<span data-ttu-id="17e72-121">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="17e72-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="17e72-122">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="17e72-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="17e72-123">-netcf</span><span class="sxs-lookup"><span data-stu-id="17e72-123">-netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)
- [<span data-ttu-id="17e72-124">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="17e72-124">-vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
