---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 52ef0b991554c800dba4320b0c64c81ddd1b0ff4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414288"
---
# <a name="-win32icon"></a><span data-ttu-id="fc924-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="fc924-102">-win32icon</span></span>
<span data-ttu-id="fc924-103">Wstawia plik. ico w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="fc924-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="fc924-104">Ten plik. ico reprezentuje plik wyjściowy w **Eksploratorze plików**.</span><span class="sxs-lookup"><span data-stu-id="fc924-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc924-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc924-105">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="fc924-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="fc924-106">Arguments</span></span>  
  
|<span data-ttu-id="fc924-107">Termin</span><span class="sxs-lookup"><span data-stu-id="fc924-107">Term</span></span>|<span data-ttu-id="fc924-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="fc924-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="fc924-109">Plik. ico, który ma zostać dodany do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="fc924-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="fc924-110">Nazwa pliku należy ująć w cudzysłów (""), jeśli zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="fc924-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc924-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc924-111">Remarks</span></span>  
 <span data-ttu-id="fc924-112">Plik. ico można utworzyć za pomocą kompilatora zasobów systemu Microsoft Windows (RC).</span><span class="sxs-lookup"><span data-stu-id="fc924-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="fc924-113">Kompilator zasobów jest wywoływany podczas kompilowania programu Visual C++owego; plik. ico jest tworzony na podstawie pliku. rc.</span><span class="sxs-lookup"><span data-stu-id="fc924-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="fc924-114">`-win32icon`Opcje i `-win32resource` wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="fc924-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="fc924-115">Zobacz [-linkresource — (Visual Basic)](linkresource.md) , aby odwołać się do .NET Framework pliku zasobów, lub [-Resource (Visual Basic)](resource.md) , aby dołączyć plik zasobów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fc924-115">See [-linkresource (Visual Basic)](linkresource.md) to reference a .NET Framework resource file, or [-resource (Visual Basic)](resource.md) to attach a .NET Framework resource file.</span></span> <span data-ttu-id="fc924-116">Aby zaimportować plik. res, zobacz temat [-win32resource](win32resource.md) .</span><span class="sxs-lookup"><span data-stu-id="fc924-116">See [-win32resource](win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="fc924-117">Aby ustawić-win32icon w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="fc924-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="fc924-118">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="fc924-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="fc924-119">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fc924-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="fc924-120">2. Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="fc924-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="fc924-121">3. Zmodyfikuj wartość w polu **ikony** .</span><span class="sxs-lookup"><span data-stu-id="fc924-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="fc924-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="fc924-122">Example</span></span>  
 <span data-ttu-id="fc924-123">Poniższy kod kompiluje `In.vb` i dołącza plik. ico, `Rf.ico` .</span><span class="sxs-lookup"><span data-stu-id="fc924-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="fc924-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc924-124">See also</span></span>

- [<span data-ttu-id="fc924-125">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc924-125">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="fc924-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="fc924-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
