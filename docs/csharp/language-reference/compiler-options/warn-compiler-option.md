---
title: -warn (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warn
helpviewer_keywords:
- warning level [C#]
- /w compiler option [C#]
- -w compiler option [C#]
- -warn compiler option [C#]
- /warn compiler option [C#]
- w compiler option [C#]
- warn compiler option [C#]
ms.assetid: 5f80ff59-4991-4382-9f9a-77da18446e71
ms.openlocfilehash: 14656fa25ea1d01339bd63efb999e938e1243db8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746423"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="7782e-102">-warn (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7782e-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="7782e-103">**-Warn** opcja określa poziom ostrzeżeń dla kompilatora do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="7782e-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7782e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7782e-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="7782e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7782e-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="7782e-106">Poziom ostrzeżeń, które mają być wyświetlane dla kompilacji: niższych numerach Pokaż tylko ostrzeżenia o wysokiej ważności; tymi o wyższych numerach Pokaż więcej ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="7782e-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="7782e-107">Prawidłowe wartości to 0-4:</span><span class="sxs-lookup"><span data-stu-id="7782e-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="7782e-108">Poziom ostrzeżeń</span><span class="sxs-lookup"><span data-stu-id="7782e-108">Warning level</span></span>|<span data-ttu-id="7782e-109">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="7782e-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="7782e-110">0</span><span class="sxs-lookup"><span data-stu-id="7782e-110">0</span></span>|<span data-ttu-id="7782e-111">Wyłącza emisji wszystkie komunikaty ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="7782e-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="7782e-112">1</span><span class="sxs-lookup"><span data-stu-id="7782e-112">1</span></span>|<span data-ttu-id="7782e-113">Wyświetla poważne ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="7782e-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="7782e-114">2</span><span class="sxs-lookup"><span data-stu-id="7782e-114">2</span></span>|<span data-ttu-id="7782e-115">Wyświetla ostrzeżenia poziomu 1 oraz pewnym ostrzeżenia mniej poważne, takie jak ostrzeżenia o ukrywaniu składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="7782e-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="7782e-116">3</span><span class="sxs-lookup"><span data-stu-id="7782e-116">3</span></span>|<span data-ttu-id="7782e-117">Wyświetla poziom ostrzeżeń 2 plus niektórych, ostrzeżenia mniej poważne, takie jak ostrzeżenia na temat wyrażeń, które zawsze przyjmowało `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="7782e-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="7782e-118">4 (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="7782e-118">4 (the default)</span></span>|<span data-ttu-id="7782e-119">Wyświetla wszystkie poziom ostrzeżeń 3. oraz ostrzeżenia informacyjne.</span><span class="sxs-lookup"><span data-stu-id="7782e-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7782e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7782e-120">Remarks</span></span>  
 <span data-ttu-id="7782e-121">Aby uzyskać informacje na temat błędu lub ostrzeżenia, możesz wyszukać kod błędu w indeksie Pomocy.</span><span class="sxs-lookup"><span data-stu-id="7782e-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="7782e-122">Aby uzyskać inny sposób uzyskać informacje na temat błędu lub ostrzeżenia, zobacz [błędy kompilatora C#](../../../csharp/language-reference/compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="7782e-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../../../csharp/language-reference/compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="7782e-123">Użyj [- warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) na traktowanie wszystkich ostrzeżeń jako błędy.</span><span class="sxs-lookup"><span data-stu-id="7782e-123">Use [-warnaserror](../../../csharp/language-reference/compiler-options/warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="7782e-124">Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) można wyłączyć niektórych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="7782e-124">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="7782e-125">**-w** jest krótka forma **-warn**.</span><span class="sxs-lookup"><span data-stu-id="7782e-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7782e-126">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7782e-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7782e-127">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="7782e-127">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="7782e-128">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="7782e-128">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7782e-129">Modyfikowanie **poziom ostrzeżeń** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7782e-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="7782e-130">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span><span class="sxs-lookup"><span data-stu-id="7782e-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7782e-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="7782e-131">Example</span></span>  
 <span data-ttu-id="7782e-132">Skompilować `in.cs` i pozwolić kompilatorowi na tylko wyświetlania ostrzeżenia poziomu 1:</span><span class="sxs-lookup"><span data-stu-id="7782e-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="7782e-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7782e-133">See Also</span></span>  

- [<span data-ttu-id="7782e-134">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7782e-134">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="7782e-135">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7782e-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
