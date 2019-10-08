---
title: -Reference (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 552fbcf920be609de83708a995a87761f6080220
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005274"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="f3dcf-102">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3dcf-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="f3dcf-103">Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3dcf-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3dcf-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="f3dcf-105">lub</span><span class="sxs-lookup"><span data-stu-id="f3dcf-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="f3dcf-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f3dcf-106">Arguments</span></span>  
  
|<span data-ttu-id="f3dcf-107">Termin</span><span class="sxs-lookup"><span data-stu-id="f3dcf-107">Term</span></span>|<span data-ttu-id="f3dcf-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="f3dcf-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="f3dcf-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-109">Required.</span></span> <span data-ttu-id="f3dcf-110">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="f3dcf-111">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3dcf-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3dcf-112">Remarks</span></span>  
 <span data-ttu-id="f3dcf-113">Importowane pliki muszą zawierać metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="f3dcf-114">Tylko typy publiczne są widoczne poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="f3dcf-115">Opcja [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) Importuje metadane z modułu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-115">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="f3dcf-116">Jeśli odwołujesz się do zestawu (zestawu A), który sam odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="f3dcf-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="f3dcf-117">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="f3dcf-118">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="f3dcf-119">Użyj [-LIBPATH](../../../visual-basic/reference/command-line-compiler/libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-119">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="f3dcf-120">Aby kompilator rozpoznawał typ w zestawie (nie w module), musi być zmuszony do rozpoznania typu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="f3dcf-121">Przykładem tego, jak można to zrobić, jest zdefiniowanie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="f3dcf-122">Inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="f3dcf-123">Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu jest nazywana kompilatorem.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="f3dcf-124">Plik odpowiedzi VBC. rsp, który odwołuje się do najczęściej używanych zestawów .NET Framework, jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="f3dcf-125">Użyj `-noconfig`, jeśli nie chcesz, aby kompilator używał VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="f3dcf-126">Krótka forma `-reference` jest `/r`.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-126">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3dcf-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3dcf-127">Example</span></span>  
 <span data-ttu-id="f3dcf-128">Następujące polecenie kompiluje plik źródłowy `Input.vb` i zestawy odwołań z `Metad1.dll` i `Metad2.dll` do utworzenia `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="f3dcf-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3dcf-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3dcf-129">See also</span></span>

- [<span data-ttu-id="f3dcf-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f3dcf-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f3dcf-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="f3dcf-131">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="f3dcf-132">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3dcf-132">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f3dcf-133">Public</span><span class="sxs-lookup"><span data-stu-id="f3dcf-133">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="f3dcf-134">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f3dcf-134">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
