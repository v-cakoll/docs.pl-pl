---
title: -main (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5f1d06bf408f13a78df503ab10fe3c57b4ff68a3
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="eb46b-102">-main (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="eb46b-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="eb46b-103">Ta opcja określa klasę, która zawiera wpis wskaż program, jeśli zawiera więcej niż jedną klasę **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="eb46b-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb46b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="eb46b-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="eb46b-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="eb46b-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="eb46b-106">Typ zawierający **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="eb46b-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb46b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb46b-107">Remarks</span></span>  
 <span data-ttu-id="eb46b-108">Jeśli Twoje kompilacji zawiera więcej niż jeden typ z [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody, można określić, którego typ zawiera **Main** metodę, która ma być używany jako punkt wejścia do programu.</span><span class="sxs-lookup"><span data-stu-id="eb46b-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="eb46b-109">Ta opcja jest przeznaczona do użytku podczas kompilowania pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="eb46b-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="eb46b-110">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="eb46b-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="eb46b-111">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="eb46b-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="eb46b-112">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb46b-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="eb46b-113">Modyfikowanie **obiekt uruchomieniowy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb46b-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="eb46b-114">Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb46b-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb46b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="eb46b-115">Example</span></span>  
 <span data-ttu-id="eb46b-116">Kompiluj `t2.cs` i `t3.cs`, określania który **Main** będzie można znaleźć metody w `Test2`:</span><span class="sxs-lookup"><span data-stu-id="eb46b-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="eb46b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eb46b-117">See Also</span></span>  
 [<span data-ttu-id="eb46b-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="eb46b-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="eb46b-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="eb46b-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
