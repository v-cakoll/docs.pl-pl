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
ms.openlocfilehash: 4c410fd7dcaae4e19043f5f858a2f75c69587311
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662273"
---
# <a name="-reference-visual-basic"></a><span data-ttu-id="91ee0-102">— Odwołanie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91ee0-102">-reference (Visual Basic)</span></span>
<span data-ttu-id="91ee0-103">Powoduje, że kompilator udostępnia informacje o typie w określonych zestawach do projektu, które są aktualnie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="91ee0-103">Causes the compiler to make type information in the specified assemblies available to the project you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ee0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="91ee0-104">Syntax</span></span>  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="91ee0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="91ee0-105">Arguments</span></span>  
  
|<span data-ttu-id="91ee0-106">Termin</span><span class="sxs-lookup"><span data-stu-id="91ee0-106">Term</span></span>|<span data-ttu-id="91ee0-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="91ee0-107">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="91ee0-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="91ee0-108">Required.</span></span> <span data-ttu-id="91ee0-109">Rozdzielana przecinkami lista nazw plików zestawu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-109">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="91ee0-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-110">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91ee0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="91ee0-111">Remarks</span></span>  
 <span data-ttu-id="91ee0-112">Pliki, które należy zaimportować musi zawierać metadane zestawu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-112">The file(s) you import must contain assembly metadata.</span></span> <span data-ttu-id="91ee0-113">Tylko typy publiczne są widoczne poza zestawem.</span><span class="sxs-lookup"><span data-stu-id="91ee0-113">Only public types are visible outside the assembly.</span></span> <span data-ttu-id="91ee0-114">[/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) opcja importuje metadane z modułu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-114">The [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) option imports metadata from a module.</span></span>  
  
 <span data-ttu-id="91ee0-115">Jeśli odwołujesz się zestaw (Assembly A) która sama odwołuje się do innego zestawu (Assembly B), należy odwołanie do zestawu B, jeśli:</span><span class="sxs-lookup"><span data-stu-id="91ee0-115">If you reference an assembly (Assembly A) which itself references another assembly (Assembly B), you need to reference Assembly B if:</span></span>  
  
-   <span data-ttu-id="91ee0-116">Typ z zestawu A dziedziczy z typu lub implementuje interfejs z zestawu B.</span><span class="sxs-lookup"><span data-stu-id="91ee0-116">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
-   <span data-ttu-id="91ee0-117">Pola, właściwości, zdarzenia lub metody, która ma typ lub parametr typu zwracanego z zestawu B zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="91ee0-117">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="91ee0-118">Użyj [- libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) określić katalog, w którym znajduje się co najmniej jeden z odwołania do zestawów.</span><span class="sxs-lookup"><span data-stu-id="91ee0-118">Use [-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="91ee0-119">Aby kompilator mógł rozpoznać typu w zestawie (nie moduł) należy wymusić do rozpoznania typu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-119">For the compiler to recognize a type in an assembly (not a module), it must be forced to resolve the type.</span></span> <span data-ttu-id="91ee0-120">Jednym z przykładów jak to zrobić, jest definiowanie wystąpienia tego typu.</span><span class="sxs-lookup"><span data-stu-id="91ee0-120">One example of how you can do this is to define an instance of the type.</span></span> <span data-ttu-id="91ee0-121">Inne metody są dostępne do rozpoznawania nazw typów w zestawie dla kompilatora.</span><span class="sxs-lookup"><span data-stu-id="91ee0-121">Other ways are available to resolve type names in an assembly for the compiler.</span></span> <span data-ttu-id="91ee0-122">Na przykład jeśli możesz dziedziczyć z typu w zestawie, nazwa typu następnie staje się znane kompilator.</span><span class="sxs-lookup"><span data-stu-id="91ee0-122">For example, if you inherit from a type in an assembly, the type name then becomes known to the compiler.</span></span>  
  
 <span data-ttu-id="91ee0-123">Plik odpowiedzi Vbc.rsp odwołania najczęściej używanych [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zestawów, jest używane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="91ee0-123">The Vbc.rsp response file, which references commonly used [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] assemblies, is used by default.</span></span> <span data-ttu-id="91ee0-124">Użyj `-noconfig` Jeśli nie chcesz, aby kompilator korzystać Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="91ee0-124">Use `-noconfig` if you do not want the compiler to use Vbc.rsp.</span></span>  
  
 <span data-ttu-id="91ee0-125">Krótkiej formy `-reference` jest `/r`.</span><span class="sxs-lookup"><span data-stu-id="91ee0-125">The short form of `-reference` is `/r`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91ee0-126">Przykład</span><span class="sxs-lookup"><span data-stu-id="91ee0-126">Example</span></span>  
 <span data-ttu-id="91ee0-127">Poniższe polecenie kompiluje plik źródłowy `Input.vb` i odwoływać się do zestawów z `Metad1.dll` i `Metad2.dll` do produkcji `Out.exe`.</span><span class="sxs-lookup"><span data-stu-id="91ee0-127">The following command compiles source file `Input.vb` and reference assemblies from `Metad1.dll` and `Metad2.dll` to produce `Out.exe`.</span></span>  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="91ee0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="91ee0-128">See also</span></span>
- [<span data-ttu-id="91ee0-129">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91ee0-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="91ee0-130">-noconfig</span><span class="sxs-lookup"><span data-stu-id="91ee0-130">-noconfig</span></span>](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [<span data-ttu-id="91ee0-131">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91ee0-131">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="91ee0-132">Public</span><span class="sxs-lookup"><span data-stu-id="91ee0-132">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="91ee0-133">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="91ee0-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
