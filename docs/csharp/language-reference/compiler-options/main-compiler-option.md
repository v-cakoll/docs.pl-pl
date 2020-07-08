---
title: -Main (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 1de3d51953b632e3881db76202b63d3f287b39fe
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051873"
---
# <a name="-main-c-compiler-options"></a><span data-ttu-id="709b7-102">-Main (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="709b7-102">-main (C# Compiler Options)</span></span>

<span data-ttu-id="709b7-103">Ta opcja określa klasę, która zawiera punkt wejścia do programu, jeśli więcej niż jedna Klasa zawiera metodę **Main** .</span><span class="sxs-lookup"><span data-stu-id="709b7-103">This option specifies the class that contains the entry point to the program, if more than one class contains a **Main** method.</span></span>

## <a name="syntax"></a><span data-ttu-id="709b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="709b7-104">Syntax</span></span>

```console
-main:class
```

## <a name="arguments"></a><span data-ttu-id="709b7-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="709b7-105">Arguments</span></span>
 `class`  
 <span data-ttu-id="709b7-106">Typ, który zawiera metodę **Main** .</span><span class="sxs-lookup"><span data-stu-id="709b7-106">The type that contains the **Main** method.</span></span>  
 <span data-ttu-id="709b7-107">Podana nazwa klasy musi być w pełni kwalifikowana; musi zawierać pełną przestrzeń nazw zawierającą klasę, a po niej nazwę klasy.</span><span class="sxs-lookup"><span data-stu-id="709b7-107">The provided class name must be fully qualified; it must include the full namespace containing the class, followed by the class name.</span></span> <span data-ttu-id="709b7-108">Na przykład, gdy metoda znajduje się `Main` wewnątrz `Program` klasy w `MyApplication.Core` przestrzeni nazw, opcja kompilatora musi mieć wartość `-main:MyApplication.Core.Program` .</span><span class="sxs-lookup"><span data-stu-id="709b7-108">For example, when the `Main` method is located inside the `Program` class in the `MyApplication.Core` namespace, the compiler option has to be `-main:MyApplication.Core.Program`.</span></span>

## <a name="remarks"></a><span data-ttu-id="709b7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="709b7-109">Remarks</span></span>

<span data-ttu-id="709b7-110">Jeśli kompilacja zawiera więcej niż jeden typ z metodą [Main](../../programming-guide/main-and-command-args/index.md) , można określić, który typ zawiera metodę **Main** , która ma być używana jako punkt wejścia do programu.</span><span class="sxs-lookup"><span data-stu-id="709b7-110">If your compilation includes more than one type with a [Main](../../programming-guide/main-and-command-args/index.md) method, you can specify which type contains the **Main** method that you want to use as the entry point into the program.</span></span>

<span data-ttu-id="709b7-111">Ta opcja jest używana podczas kompilowania pliku *. exe* .</span><span class="sxs-lookup"><span data-stu-id="709b7-111">This option is for use when compiling an *.exe* file.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="709b7-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="709b7-112">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="709b7-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="709b7-113">Open the project's **Properties** page.</span></span>

2. <span data-ttu-id="709b7-114">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="709b7-114">Click the **Application** property page.</span></span>

3. <span data-ttu-id="709b7-115">Zmodyfikuj właściwość **obiektu uruchomieniowego** .</span><span class="sxs-lookup"><span data-stu-id="709b7-115">Modify the **Startup object** property.</span></span>

    <span data-ttu-id="709b7-116">Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.StartupObject%2A> .</span><span class="sxs-lookup"><span data-stu-id="709b7-116">To set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.</span></span>

### <a name="to-set-this-compiler-option-by-manually-editing-the-csproj-file"></a><span data-ttu-id="709b7-117">Aby ustawić tę opcję kompilatora, ręcznie edytując plik *. csproj*</span><span class="sxs-lookup"><span data-stu-id="709b7-117">To set this compiler option by manually editing the *.csproj* file</span></span>

<span data-ttu-id="709b7-118">Tę opcję można ustawić, edytując plik. csproj i dodając element `StartupObject` w `PropertyGroup` sekcji.</span><span class="sxs-lookup"><span data-stu-id="709b7-118">You can set this option by editing the .csproj file and adding an element `StartupObject` inside the `PropertyGroup` section.</span></span> <span data-ttu-id="709b7-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="709b7-119">For example:</span></span>

```xml
  <PropertyGroup>
    ...
    <StartupObject>MyApplication.Core.Program</StartupObject>
  </PropertyGroup>
```

## <a name="example"></a><span data-ttu-id="709b7-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="709b7-120">Example</span></span>

<span data-ttu-id="709b7-121">Kompiluj `t2.cs` i `t3.cs` , określając, że metoda **Main** zostanie znaleziona w `Test2` :</span><span class="sxs-lookup"><span data-stu-id="709b7-121">Compile `t2.cs` and `t3.cs`, specifying that the **Main** method will be found in `Test2`:</span></span>

```console
csc t2.cs t3.cs -main:Test2
```

## <a name="see-also"></a><span data-ttu-id="709b7-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="709b7-122">See also</span></span>

- [<span data-ttu-id="709b7-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="709b7-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="709b7-124">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="709b7-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
