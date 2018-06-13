---
title: -main (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 2df02200578979f9a613f43dc92cc9e7b0cb430e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212423"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="7365a-102">-main (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7365a-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="7365a-103">Ta opcja określa klasę, która zawiera wpis wskaż program, jeśli zawiera więcej niż jedną klasę **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="7365a-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7365a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7365a-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="7365a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7365a-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="7365a-106">Typ zawierający **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="7365a-106">The type that contains the **Main** method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7365a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7365a-107">Remarks</span></span>  
 <span data-ttu-id="7365a-108">Jeśli Twoje kompilacji zawiera więcej niż jeden typ z [Main](../../../csharp/programming-guide/main-and-command-args/index.md) metody, można określić, którego typ zawiera **Main** metodę, która ma być używany jako punkt wejścia do programu.</span><span class="sxs-lookup"><span data-stu-id="7365a-108">If your compilation includes more than one type with a [Main](../../../csharp/programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="7365a-109">Ta opcja jest przeznaczona do użytku podczas kompilowania pliku .exe.</span><span class="sxs-lookup"><span data-stu-id="7365a-109">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7365a-110">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7365a-110">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7365a-111">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="7365a-111">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="7365a-112">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="7365a-112">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="7365a-113">Modyfikowanie **obiekt uruchomieniowy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7365a-113">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="7365a-114">Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="7365a-114">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7365a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7365a-115">Example</span></span>  
 <span data-ttu-id="7365a-116">Kompiluj `t2.cs` i `t3.cs`, określania który **Main** będzie można znaleźć metody w `Test2`:</span><span class="sxs-lookup"><span data-stu-id="7365a-116">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="7365a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7365a-117">See Also</span></span>  
 [<span data-ttu-id="7365a-118">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7365a-118">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7365a-119">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7365a-119">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
