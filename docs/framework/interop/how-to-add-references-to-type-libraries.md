---
title: 'Instrukcje: Dodaj odwołania do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 71c2a6b183890aa9625dcffbef59d14c27ebe754
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219403"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="6f394-102">Instrukcje: Dodaj odwołania do bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="6f394-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="6f394-103">Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane, gdy użytkownik dodaje odnośnik do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="6f394-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="6f394-104">Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio korzysta z istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6f394-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="6f394-105">Aby dodać odwołanie do biblioteki typów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6f394-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="6f394-106">Zainstaluj plik COM DLL lub EXE na komputerze, chyba, że plik Windows Setup.exe wykonuje instalację.</span><span class="sxs-lookup"><span data-stu-id="6f394-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="6f394-107">Wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="6f394-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="6f394-108">Wybierz w Menedżerze odwołań **COM**.</span><span class="sxs-lookup"><span data-stu-id="6f394-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="6f394-109">Wybierz bibliotekę typów, z listy lub Przeglądaj w poszukiwaniu pliku .tlb.</span><span class="sxs-lookup"><span data-stu-id="6f394-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="6f394-110">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="6f394-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="6f394-111">W Eksploratorze rozwiązań Otwórz menu skrótów dla odwołania do właśnie dodane, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="6f394-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="6f394-112">W **właściwości** okna, upewnij się, że **Osadź typy współdziałania** właściwość jest ustawiona na **True**.</span><span class="sxs-lookup"><span data-stu-id="6f394-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="6f394-113">To powoduje, że Visual Studio w celu osadzenia informacji o typie dla typów modelu COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="6f394-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6f394-114">Okno dialogowe i menu opcji w oknie mogą się różnić w zależności od wersji programu Visual Studio jest używany.</span><span class="sxs-lookup"><span data-stu-id="6f394-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="6f394-115">Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="6f394-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="6f394-116">Generowanie zestawu międzyoperacyjnego, zgodnie z opisem w [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="6f394-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="6f394-117">Użyj [/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) — opcja kompilatora z nazwą zestawu międzyoperacyjnego do osadzenia informacji o typie dla modelu COM, typy w swoje pliki wykonywalne.</span><span class="sxs-lookup"><span data-stu-id="6f394-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f394-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6f394-118">See also</span></span>
- [<span data-ttu-id="6f394-119">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="6f394-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="6f394-120">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f394-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="6f394-121">Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="6f394-121">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (C#)</span></span>](../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies.md)
- [<span data-ttu-id="6f394-122">Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f394-122">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)
- [<span data-ttu-id="6f394-123">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="6f394-123">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (C#)</span></span>](/docs/csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md) 
- [<span data-ttu-id="6f394-124">Przewodnik: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f394-124">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](/docs/visual-basic/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-vs.md)
- [<span data-ttu-id="6f394-125">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6f394-125">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="6f394-126">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f394-126">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
