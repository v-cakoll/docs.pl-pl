---
title: 'Instrukcje: Dodawanie odwołań do bibliotek typów'
description: Zapoznaj się z tematem Dodawanie odwołań do bibliotek typów w programie Visual Studio lub dla kompilacji wiersza polecenia.
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: a3c24385c9cc7debe95aa10369b050897415bc46
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617434"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="c6ac0-103">Instrukcje: Dodawanie odwołań do bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="c6ac0-103">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="c6ac0-104">Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane podczas dodawania odwołania do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-104">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="c6ac0-105">Jeśli jest dostępny podstawowy zestaw międzyoperacyjny, program Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-105">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="c6ac0-106">Aby dodać odwołanie do biblioteki typów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6ac0-106">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="c6ac0-107">Zainstaluj plik DLL COM lub EXE na komputerze, chyba że plik Setup.exe systemu Windows przeprowadzi instalację.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-107">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="c6ac0-108">Wybierz **projekt**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-108">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="c6ac0-109">W Menedżerze odwołań wybierz **com**.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-109">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="c6ac0-110">Wybierz bibliotekę typów z listy lub Wyszukaj plik. tlb.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-110">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="c6ac0-111">Wybierz przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-111">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="c6ac0-112">W Eksplorator rozwiązań otwórz menu skrótów dla właśnie dodanego odwołania, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-112">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="c6ac0-113">W oknie **Właściwości** upewnij się, że właściwość **Osadź typy** współdziałania ma **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-113">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="c6ac0-114">Powoduje to, że program Visual Studio osadzi informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-114">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6ac0-115">Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-115">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="c6ac0-116">Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c6ac0-116">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="c6ac0-117">Generowanie zestawu międzyoperacyjnego zgodnie z opisem w temacie [How to: Generate Assembly Interop from Library Type](how-to-generate-interop-assemblies-from-type-libraries.md)librarys.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-117">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="c6ac0-118">Użyj opcji [-link (opcje kompilatora C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) z nazwą zestawu międzyoperacyjnego, aby osadzić informacje o typie dla typów com w plikach wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="c6ac0-118">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6ac0-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6ac0-119">See also</span></span>

- [<span data-ttu-id="c6ac0-120">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="c6ac0-120">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="c6ac0-121">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c6ac0-121">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="c6ac0-122">Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6ac0-122">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="c6ac0-123">-Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="c6ac0-123">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="c6ac0-124">-Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6ac0-124">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
