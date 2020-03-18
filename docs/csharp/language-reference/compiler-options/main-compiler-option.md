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
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602727"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="d7c0e-102">-main (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d7c0e-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="d7c0e-103">Ta opcja określa klasę, która zawiera punkt wejścia do programu, jeśli więcej niż jedna klasa zawiera **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c0e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7c0e-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="d7c0e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d7c0e-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="d7c0e-106">Typ, który zawiera **Main** metody.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="d7c0e-107">Podana nazwa klasy musi być w pełni kwalifikowana; musi zawierać pełną przestrzeń nazw zawierającą klasę, a następnie nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="d7c0e-108">Na przykład gdy `Main` metoda znajduje `Program` się wewnątrz `MyApplication.Core` klasy w przestrzeni nazw, `-main:MyApplication.Core.Program`opcja kompilatora musi być .</span><span class="sxs-lookup"><span data-stu-id="d7c0e-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d7c0e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d7c0e-109">Remarks</span></span>  
 <span data-ttu-id="d7c0e-110">Jeśli kompilacja zawiera więcej niż jeden typ z [Main](../../programming-guide/main-and-command-args/index.md) metody, można określić, który typ zawiera **Main** metoda, która ma być używana jako punkt wejścia do programu.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="d7c0e-111">Ta opcja jest używana podczas kompilowania pliku exe.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d7c0e-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d7c0e-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="d7c0e-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="d7c0e-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="d7c0e-114">Kliknij stronę **właściwości Application.**</span><span class="sxs-lookup"><span data-stu-id="d7c0e-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="d7c0e-115">Zmodyfikuj właściwość **Startup object.**</span><span class="sxs-lookup"><span data-stu-id="d7c0e-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="d7c0e-116">Aby programowo ustawić tę opcję <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="d7c0e-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c0e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7c0e-117">Example</span></span>  
 <span data-ttu-id="d7c0e-118">Skompiluj `t2.cs` i `t3.cs`, określając, że metoda **główna** zostanie znaleziona w `Test2`:</span><span class="sxs-lookup"><span data-stu-id="d7c0e-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="d7c0e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7c0e-119">See also</span></span>

- [<span data-ttu-id="d7c0e-120">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="d7c0e-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="d7c0e-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="d7c0e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
