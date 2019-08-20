---
title: -warn (C# opcje kompilatora)
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
ms.openlocfilehash: 5b05e944a37e16fc1fcc422271be00c09a271a33
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602407"
---
# <a name="-warn-c-compiler-options"></a><span data-ttu-id="4262c-102">-warn (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="4262c-102">-warn (C# Compiler Options)</span></span>
<span data-ttu-id="4262c-103">Opcja **-warn** określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="4262c-103">The **-warn** option specifies the warning level for the compiler to display.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4262c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4262c-104">Syntax</span></span>  
  
```console  
-warn:option  
```  
  
## <a name="arguments"></a><span data-ttu-id="4262c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="4262c-105">Arguments</span></span>  
 `option`  
 <span data-ttu-id="4262c-106">Poziom ostrzeżeń, który ma być wyświetlany dla kompilacji: Niższe numery pokazują tylko ostrzeżenia o wysokiej ważności; wyższe liczby zawierają więcej ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="4262c-106">The warning level you want displayed for the compilation: Lower numbers show only high severity warnings; higher numbers show more warnings.</span></span> <span data-ttu-id="4262c-107">Prawidłowe wartości to 0-4:</span><span class="sxs-lookup"><span data-stu-id="4262c-107">Valid values are 0-4:</span></span>  
  
|<span data-ttu-id="4262c-108">Poziom ostrzeżeń</span><span class="sxs-lookup"><span data-stu-id="4262c-108">Warning level</span></span>|<span data-ttu-id="4262c-109">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="4262c-109">Meaning</span></span>|  
|-------------------|-------------|  
|<span data-ttu-id="4262c-110">0</span><span class="sxs-lookup"><span data-stu-id="4262c-110">0</span></span>|<span data-ttu-id="4262c-111">Wyłącza emisję wszystkich komunikatów ostrzegawczych.</span><span class="sxs-lookup"><span data-stu-id="4262c-111">Turns off emission of all warning messages.</span></span>|  
|<span data-ttu-id="4262c-112">1</span><span class="sxs-lookup"><span data-stu-id="4262c-112">1</span></span>|<span data-ttu-id="4262c-113">Wyświetla poważne komunikaty ostrzegawcze.</span><span class="sxs-lookup"><span data-stu-id="4262c-113">Displays severe warning messages.</span></span>|  
|<span data-ttu-id="4262c-114">2</span><span class="sxs-lookup"><span data-stu-id="4262c-114">2</span></span>|<span data-ttu-id="4262c-115">Wyświetla ostrzeżenia poziomu 1 i pewne mniej surowe ostrzeżenia, takie jak ostrzeżenia dotyczące ukrywania elementów członkowskich klasy.</span><span class="sxs-lookup"><span data-stu-id="4262c-115">Displays level 1 warnings plus certain, less-severe warnings, such as warnings about hiding class members.</span></span>|  
|<span data-ttu-id="4262c-116">3</span><span class="sxs-lookup"><span data-stu-id="4262c-116">3</span></span>|<span data-ttu-id="4262c-117">Wyświetla ostrzeżenia poziomu 2 oraz pewne mniej surowe ostrzeżenia, takie jak ostrzeżenia dotyczące wyrażeń, które zawsze są oceniane do `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="4262c-117">Displays level 2 warnings plus certain, less-severe warnings, such as warnings about expressions that always evaluate to `true` or `false`.</span></span>|  
|<span data-ttu-id="4262c-118">4 (wartość domyślna)</span><span class="sxs-lookup"><span data-stu-id="4262c-118">4 (the default)</span></span>|<span data-ttu-id="4262c-119">Wyświetla wszystkie ostrzeżenia poziomu 3 i ostrzeżenia informacyjne.</span><span class="sxs-lookup"><span data-stu-id="4262c-119">Displays all level 3 warnings plus informational warnings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4262c-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4262c-120">Remarks</span></span>  
 <span data-ttu-id="4262c-121">Aby uzyskać informacje o błędzie lub ostrzeżeniu, można wyszukać kod błędu w indeksie pomocy.</span><span class="sxs-lookup"><span data-stu-id="4262c-121">To get information about an error or warning, you can look up the error code in the Help Index.</span></span> <span data-ttu-id="4262c-122">Aby uzyskać informacje dotyczące błędu lub ostrzeżenia, zobacz [ C# błędy kompilatora](../compiler-messages/index.md).</span><span class="sxs-lookup"><span data-stu-id="4262c-122">For other ways to get information about an error or warning, see [C# Compiler Errors](../compiler-messages/index.md).</span></span>  
  
 <span data-ttu-id="4262c-123">Użyj opcji [-warnaserror —](./warnaserror-compiler-option.md) , aby traktować wszystkie ostrzeżenia jako błędy.</span><span class="sxs-lookup"><span data-stu-id="4262c-123">Use [-warnaserror](./warnaserror-compiler-option.md) to treat all warnings as errors.</span></span> <span data-ttu-id="4262c-124">Użyj [-nowarn](./nowarn-compiler-option.md) , aby wyłączyć niektóre ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="4262c-124">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
 <span data-ttu-id="4262c-125">**-w** jest krótką formą **-warn**.</span><span class="sxs-lookup"><span data-stu-id="4262c-125">**-w** is the short form of **-warn**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="4262c-126">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4262c-126">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="4262c-127">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="4262c-127">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="4262c-128">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="4262c-128">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="4262c-129">Zmodyfikuj właściwość **poziom ostrzeżeń** .</span><span class="sxs-lookup"><span data-stu-id="4262c-129">Modify the **Warning Level** property.</span></span>  
  
 <span data-ttu-id="4262c-130">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="4262c-130">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.WarningLevel%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4262c-131">Przykład</span><span class="sxs-lookup"><span data-stu-id="4262c-131">Example</span></span>  
 <span data-ttu-id="4262c-132">Kompiluj `in.cs` i czy kompilator wyświetla tylko ostrzeżenia poziomu 1:</span><span class="sxs-lookup"><span data-stu-id="4262c-132">Compile `in.cs` and have the compiler only display level 1 warnings:</span></span>  
  
```console  
csc -warn:1 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="4262c-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4262c-133">See also</span></span>

- [<span data-ttu-id="4262c-134">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="4262c-134">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="4262c-135">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4262c-135">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
