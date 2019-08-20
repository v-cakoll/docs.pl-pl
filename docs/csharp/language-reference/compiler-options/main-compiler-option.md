---
title: -Main (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602727"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="5086f-102">-Main (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="5086f-102">-main (C# Compiler Options)</span></span>
<span data-ttu-id="5086f-103">Ta opcja określa klasę, która zawiera punkt wejścia do programu, jeśli więcej niż jedna Klasa zawiera metodę **Main** .</span><span class="sxs-lookup"><span data-stu-id="5086f-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5086f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5086f-104">Syntax</span></span>  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a><span data-ttu-id="5086f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5086f-105">Arguments</span></span>  
 `class`  
 <span data-ttu-id="5086f-106">Typ, który zawiera metodę **Main** .</span><span class="sxs-lookup"><span data-stu-id="5086f-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="5086f-107">Podana nazwa klasy musi być w pełni kwalifikowana; musi zawierać pełną przestrzeń nazw zawierającą klasę, a po niej nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="5086f-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="5086f-108">`Main` Na przykład, gdy metoda znajduje się `Program` wewnątrz klasy w `MyApplication.Core` przestrzeni nazw, opcja kompilatora musi mieć `-main:MyApplication.Core.Program`wartość.</span><span class="sxs-lookup"><span data-stu-id="5086f-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="5086f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5086f-109">Remarks</span></span>  
 <span data-ttu-id="5086f-110">Jeśli kompilacja zawiera więcej niż jeden typ z metodą [Main](../../programming-guide/main-and-command-args/index.md) , można określić, który typ zawiera metodę **Main** , która ma być używana jako punkt wejścia do programu.</span><span class="sxs-lookup"><span data-stu-id="5086f-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>  
  
 <span data-ttu-id="5086f-111">Ta opcja jest używana podczas kompilowania pliku. exe.</span><span class="sxs-lookup"><span data-stu-id="5086f-111">This option is for use when compiling an .exe file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5086f-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5086f-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="5086f-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="5086f-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="5086f-114">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="5086f-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="5086f-115">Zmodyfikuj właściwość **obiektu uruchomieniowego** .</span><span class="sxs-lookup"><span data-stu-id="5086f-115">Modify the **Startup object** property.</span></span>  
  
     <span data-ttu-id="5086f-116">Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span><span class="sxs-lookup"><span data-stu-id="5086f-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5086f-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="5086f-117">Example</span></span>  
 <span data-ttu-id="5086f-118">Kompiluj `t2.cs` `Test2`i `t3.cs`, określając, że metoda **Main** zostanie znaleziona w:</span><span class="sxs-lookup"><span data-stu-id="5086f-118">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a><span data-ttu-id="5086f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5086f-119">See also</span></span>

- [<span data-ttu-id="5086f-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="5086f-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="5086f-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5086f-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
