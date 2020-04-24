---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005502"
---
# <a name="-main"></a><span data-ttu-id="4e33e-102">-main</span><span class="sxs-lookup"><span data-stu-id="4e33e-102">-main</span></span>
<span data-ttu-id="4e33e-103">Określa klasę lub moduł, który zawiera `Sub Main` procedurę.</span><span class="sxs-lookup"><span data-stu-id="4e33e-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e33e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4e33e-104">Syntax</span></span>  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e33e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4e33e-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="4e33e-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="4e33e-106">Required.</span></span> <span data-ttu-id="4e33e-107">Nazwa klasy lub modułu, która zawiera `Sub Main` procedurę, która ma zostać wywołana podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="4e33e-107">The name of the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="4e33e-108">Może to być w formie **Main: module** lub **-Main: Namespace. module**.</span><span class="sxs-lookup"><span data-stu-id="4e33e-108">This may be in the form **-main:module** or **-main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e33e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4e33e-109">Remarks</span></span>  
 <span data-ttu-id="4e33e-110">Użyj tej opcji, gdy tworzysz plik wykonywalny lub program wykonywalny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4e33e-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="4e33e-111">Jeśli opcja **-Main** zostanie pominięta, kompilator wyszukuje prawidłowe udostępnianie `Sub Main` we wszystkich publicznych klasach i modułach.</span><span class="sxs-lookup"><span data-stu-id="4e33e-111">If the **-main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="4e33e-112">Zapoznaj się z [główną procedurą w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) , aby poznać różne formy `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="4e33e-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="4e33e-113">Gdy `location` jest klasą, która dziedziczy <xref:System.Windows.Forms.Form>z, kompilator dostarcza domyślną `Main` procedurę, która uruchamia aplikację, jeśli Klasa nie `Main` ma procedury.</span><span class="sxs-lookup"><span data-stu-id="4e33e-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="4e33e-114">Dzięki temu można kompilować kod w wierszu polecenia, który został utworzony w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="4e33e-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="4e33e-115">Aby ustawić — Main w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4e33e-115">To set -main in the Visual Studio integrated development environment</span></span>  
  
1. <span data-ttu-id="4e33e-116">Zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="4e33e-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4e33e-117">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4e33e-117">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="4e33e-118">Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="4e33e-118">Click the **Application** tab.</span></span>  
  
3. <span data-ttu-id="4e33e-119">Upewnij się, że pole wyboru **Włącz platformę aplikacji** nie jest zaznaczone.</span><span class="sxs-lookup"><span data-stu-id="4e33e-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4. <span data-ttu-id="4e33e-120">Zmodyfikuj wartość w polu **obiekt startowy** .</span><span class="sxs-lookup"><span data-stu-id="4e33e-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e33e-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="4e33e-121">Example</span></span>  
 <span data-ttu-id="4e33e-122">Poniższy `T2.vb` kod kompiluje `T3.vb`i, określając, że `Sub Main` procedura zostanie znaleziona w `Test2` klasie.</span><span class="sxs-lookup"><span data-stu-id="4e33e-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="4e33e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4e33e-123">See also</span></span>

- [<span data-ttu-id="4e33e-124">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e33e-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="4e33e-125">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e33e-125">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="4e33e-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="4e33e-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="4e33e-127">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4e33e-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
