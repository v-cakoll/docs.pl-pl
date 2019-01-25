---
title: -główny
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 355267331eda73ab4c32ec27dbba1d82d729420f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638785"
---
# <a name="-main"></a><span data-ttu-id="c7729-102">-główny</span><span class="sxs-lookup"><span data-stu-id="c7729-102">-main</span></span>
<span data-ttu-id="c7729-103">Określa klasę lub moduł, który zawiera `Sub Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="c7729-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7729-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c7729-104">Syntax</span></span>  
  
```  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="c7729-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c7729-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="c7729-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="c7729-106">Required.</span></span> <span data-ttu-id="c7729-107">Nazwa klasy lub moduł, który zawiera `Sub Main` procedury wywoływanej po uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="c7729-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="c7729-108">Może to być w formie **-main: moduł** lub **-main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="c7729-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7729-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c7729-109">Remarks</span></span>  
 <span data-ttu-id="c7729-110">Użyj tej opcji, podczas tworzenia pliku wykonywalnego lub program wykonywalny Windows.</span><span class="sxs-lookup"><span data-stu-id="c7729-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="c7729-111">Jeśli **-głównego** zostanie pominięta opcja, kompilator szuka prawidłową udostępnione `Sub Main` we wszystkich publiczne klasy i moduły.</span><span class="sxs-lookup"><span data-stu-id="c7729-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="c7729-112">Zobacz [procedura Main w języku Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) dyskusję na temat różnych metod `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="c7729-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="c7729-113">Gdy `location` to klasa, która dziedziczy po elemencie <xref:System.Windows.Forms.Form>, kompilator udostępnia domyślny `Main` procedury, która uruchamia aplikację, jeśli nie ma klasy `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="c7729-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="c7729-114">Dzięki temu można skompilować kod w wierszu polecenia, który został utworzony w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="c7729-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="c7729-115">Aby ustawić — główny w programie Visual Studio zintegrowanego środowiska programistycznego</span><span class="sxs-lookup"><span data-stu-id="c7729-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="c7729-116">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c7729-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="c7729-117">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c7729-117">On the **Project** menu, click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c7729-118">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="c7729-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="c7729-119">Upewnij się, że **struktury aplikacji Włącz** nie zaznaczono pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="c7729-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="c7729-120">Zmodyfikuj wartość w **obiekt początkowy** pole.</span><span class="sxs-lookup"><span data-stu-id="c7729-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7729-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7729-121">Example</span></span>  
 <span data-ttu-id="c7729-122">Poniższy kod kompiluje `T2.vb` i `T3.vb`, określania, `Sub Main` procedurę można znaleźć w `Test2` klasy.</span><span class="sxs-lookup"><span data-stu-id="c7729-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7729-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7729-123">See also</span></span>
- [<span data-ttu-id="c7729-124">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7729-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="c7729-125">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7729-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="c7729-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="c7729-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="c7729-127">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7729-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
