---
title: -reference
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 633b457106203e213f5d30003e576b7e8132f4d2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400490"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="2a1e0-102">-Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a1e0-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="2a1e0-103">Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach, które są dostępne dla aktualnie kompilowanego projektu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a1e0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a1e0-104">Syntax</span></span>  
  
```console  
-reference:fileList  
```

<span data-ttu-id="2a1e0-105">lub</span><span class="sxs-lookup"><span data-stu-id="2a1e0-105">or</span></span>

```console
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="2a1e0-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2a1e0-106">Arguments</span></span>  
  
|<span data-ttu-id="2a1e0-107">Termin</span><span class="sxs-lookup"><span data-stu-id="2a1e0-107">Term</span></span>|<span data-ttu-id="2a1e0-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="2a1e0-108">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="2a1e0-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-109">Required.</span></span> <span data-ttu-id="2a1e0-110">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-110">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="2a1e0-111">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-111">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a1e0-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a1e0-112">Remarks</span></span>  
 <span data-ttu-id="2a1e0-113">Importowane pliki muszą zawierać metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-113">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="2a1e0-114">Tylko typy publiczne są widoczne poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-114">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="2a1e0-115">Opcja [-addmodule](addmodule.md) Importuje metadane z modułu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-115">The [-addmodule](addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="2a1e0-116">Jeśli odwołujesz się do zestawu (zestawu A), który sam odwołuje się do innego zestawu (zestawu B), należy odwołać się do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="2a1e0-116">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="2a1e0-117">Typ z zestawu A dziedziczy po typie lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-117">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="2a1e0-118">Wywołano pole, właściwość, zdarzenie lub metodę z typem zwracanym lub typem parametru z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-118">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="2a1e0-119">Użyj [-LIBPATH](libpath.md) , aby określić katalog, w którym znajduje się co najmniej jedno odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-119">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="2a1e0-120">Aby kompilator rozpoznawał typ w zestawie (nie w module), musi być zmuszony do rozpoznania typu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-120">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="2a1e0-121">Przykładem tego, jak można to zrobić, jest zdefiniowanie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-121">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="2a1e0-122">Inne sposoby rozpoznawania nazw typów w zestawie dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-122">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="2a1e0-123">Na przykład, jeśli dziedziczysz z typu w zestawie, nazwa typu jest nazywana kompilatorem.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-123">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="2a1e0-124">Plik odpowiedzi VBC. rsp, który odwołuje się do najczęściej używanych zestawów .NET Framework, jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-124">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="2a1e0-125">Użyj, `-noconfig` Jeśli nie chcesz, aby kompilator używał VBC. rsp.</span><span class="sxs-lookup"><span data-stu-id="2a1e0-125">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="2a1e0-126">Krótka forma `-reference` to `-r` .</span><span class="sxs-lookup"><span data-stu-id="2a1e0-126">The short form of `-reference` is `-r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a1e0-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a1e0-127">Example</span></span>  
 <span data-ttu-id="2a1e0-128">Poniższe polecenie kompiluje plik źródłowy `Input.vb` i zestawy odwołań z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe` .</span><span class="sxs-lookup"><span data-stu-id="2a1e0-128">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2a1e0-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a1e0-129">See also</span></span>

- [<span data-ttu-id="2a1e0-130">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2a1e0-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="2a1e0-131">-noconfig</span><span class="sxs-lookup"><span data-stu-id="2a1e0-131">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="2a1e0-132">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a1e0-132">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="2a1e0-133">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="2a1e0-133">Public</span></span>](../../language-reference/modifiers/public.md)
- [<span data-ttu-id="2a1e0-134">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="2a1e0-134">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
