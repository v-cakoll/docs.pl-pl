---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5bb11bc62e951339113f4b48e98e05362490ca1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="main"></a><span data-ttu-id="e084d-102">/main</span><span class="sxs-lookup"><span data-stu-id="e084d-102">/main</span></span>
<span data-ttu-id="e084d-103">Określa klasę lub moduł, który zawiera `Sub Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="e084d-103">Specifies the class or module that contains the `Sub Main` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e084d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e084d-104">Syntax</span></span>  
  
```  
/main:location  
```  
  
## <a name="arguments"></a><span data-ttu-id="e084d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e084d-105">Arguments</span></span>  
 `location`  
 <span data-ttu-id="e084d-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e084d-106">Required.</span></span> <span data-ttu-id="e084d-107">Pełnej kwalifikacji w klasie lub moduł, który zawiera `Sub Main` procedury wywoływanej po uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="e084d-107">A full qualification to the class or module that contains the `Sub Main` procedure to be called when the program starts.</span></span> <span data-ttu-id="e084d-108">Może to być w formie **/main:module** lub **/main:namespace.module**.</span><span class="sxs-lookup"><span data-stu-id="e084d-108">This may be in the form **/main:module** or **/main:namespace.module**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e084d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e084d-109">Remarks</span></span>  
 <span data-ttu-id="e084d-110">Użyj tej opcji, podczas tworzenia pliku wykonywalnego lub program wykonywalny systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e084d-110">Use this option when you create an executable file or Windows executable program.</span></span> <span data-ttu-id="e084d-111">Jeśli **/main** pominięto opcja, kompilator szuka prawidłowej udostępnionych `Sub Main` we wszystkich publicznych klasy i moduły.</span><span class="sxs-lookup"><span data-stu-id="e084d-111">If the **/main** option is omitted, the compiler searches for a valid shared `Sub Main` in all public classes and modules.</span></span>  
  
 <span data-ttu-id="e084d-112">Zobacz [Main procedury w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) omówienie różne formy `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="e084d-112">See [Main Procedure in Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) for a discussion of the various forms of the `Main` procedure.</span></span>  
  
 <span data-ttu-id="e084d-113">Gdy `location` jest klasa, która dziedziczy <xref:System.Windows.Forms.Form>, kompilator udostępnia domyślny `Main` procedury, która uruchamia aplikację, jeśli nie ma klasy `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="e084d-113">When `location` is a class that inherits from <xref:System.Windows.Forms.Form>, the compiler provides a default `Main` procedure that starts the application if the class has no `Main` procedure.</span></span> <span data-ttu-id="e084d-114">Dzięki temu można skompilować kodu w wierszu polecenia, który został utworzony w środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="e084d-114">This lets you compile code at the command line that was created in the development environment.</span></span>  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a><span data-ttu-id="e084d-115">Aby ustawić/main w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="e084d-115">To set /main in the Visual Studio integrated development environment</span></span>  
  
1.  <span data-ttu-id="e084d-116">Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="e084d-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e084d-117">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e084d-117">On the **Project** menu, click **Properties**.</span></span>  
  
       
  
2.  <span data-ttu-id="e084d-118">Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="e084d-118">Click the **Application** tab.</span></span>  
  
3.  <span data-ttu-id="e084d-119">Upewnij się, że **struktury aplikacji Włącz** nie zaznaczono pola wyboru.</span><span class="sxs-lookup"><span data-stu-id="e084d-119">Make sure the **Enable application framework** check box is not checked.</span></span>  
  
4.  <span data-ttu-id="e084d-120">Zmodyfikuj wartość w **obiekt uruchomieniowy** pole.</span><span class="sxs-lookup"><span data-stu-id="e084d-120">Modify the value in the **Startup object** box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e084d-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="e084d-121">Example</span></span>  
 <span data-ttu-id="e084d-122">Poniższy kod kompiluje `T2.vb` i `T3.vb`, określania który `Sub Main` procedury zostaną znalezione w `Test2` klasy.</span><span class="sxs-lookup"><span data-stu-id="e084d-122">The following code compiles `T2.vb` and `T3.vb`, specifying that the `Sub Main` procedure will be found in the `Test2` class.</span></span>  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="e084d-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e084d-123">See Also</span></span>  
 [<span data-ttu-id="e084d-124">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e084d-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="e084d-125">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e084d-125">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="e084d-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e084d-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="e084d-127">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e084d-127">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
