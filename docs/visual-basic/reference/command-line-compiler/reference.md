---
title: — Odwołanie (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 2394a23ddd59d09ce53c78fc4486fc5bae9e8516
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583362"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="d859f-102">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d859f-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="d859f-103">Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach do projektu, które są aktualnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d859f-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d859f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d859f-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d859f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d859f-105">Arguments</span></span>  
  
|<span data-ttu-id="d859f-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d859f-106">Term</span></span>|<span data-ttu-id="d859f-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d859f-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="d859f-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d859f-108">Required.</span></span> <span data-ttu-id="d859f-109">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="d859f-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="d859f-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="d859f-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d859f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d859f-111">Remarks</span></span>  
 <span data-ttu-id="d859f-112">Pliki, które należy zaimportować musi zawierać metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="d859f-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="d859f-113">Tylko typy publiczne są widoczne poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="d859f-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="d859f-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.</span><span class="sxs-lookup"><span data-stu-id="d859f-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="d859f-115">Jeśli odwołujesz się zestaw (Assembly A) która sama odwołuje się do innego zestawu (Assembly B), należy odwołanie do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="d859f-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
- <span data-ttu-id="d859f-116">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="d859f-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="d859f-117">Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="d859f-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="d859f-118">Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="d859f-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="d859f-119">Aby kompilator mógł rozpoznać typu w zestawie (nie moduł) należy wymusić do rozpoznania typu.</span><span class="sxs-lookup"><span data-stu-id="d859f-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="d859f-120">Jednym z przykładów jak to zrobić, jest definiowanie wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="d859f-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="d859f-121">Inne metody są dostępne do rozpoznawania nazw typów w zestawie dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d859f-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="d859f-122">Na przykład jeśli możesz dziedziczyć z typu w zestawie, nazwa typu następnie staje się znane kompilator.</span><span class="sxs-lookup"><span data-stu-id="d859f-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="d859f-123">Plik odpowiedzi Vbc.rsp, która odwołuje się do powszechnie stosowane zestawów .NET Framework, jest używany domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d859f-123">The Vbc.rsp response file, which references commonly used .NET Framework assemblies, is used by default.</span></span> <span data-ttu-id="d859f-124">Użyj `-noconfig` Jeśli nie chcesz, aby kompilator korzystać Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="d859f-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="d859f-125">Krótkiej formy `-reference` jest `/r`.</span><span class="sxs-lookup"><span data-stu-id="d859f-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d859f-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="d859f-126">Example</span></span>  
 <span data-ttu-id="d859f-127">Poniższe polecenie kompiluje plik źródłowy `Input.vb` i odwoływać się do zestawów z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="d859f-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d859f-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d859f-128">See also</span></span>

- [<span data-ttu-id="d859f-129">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d859f-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d859f-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="d859f-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="d859f-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d859f-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="d859f-132">Public</span><span class="sxs-lookup"><span data-stu-id="d859f-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="d859f-133">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d859f-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
