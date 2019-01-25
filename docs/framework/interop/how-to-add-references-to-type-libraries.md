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
ms.openlocfilehash: ebd7599205206e026c7de7b4e7bc2e5352771bd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522222"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="27d68-102">Instrukcje: Dodaj odwołania do bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="27d68-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="27d68-103">Program Visual Studio generuje zestaw międzyoperacyjny zawierający metadane, gdy użytkownik dodaje odnośnik do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="27d68-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="27d68-104">Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio korzysta z istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="27d68-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="27d68-105">Aby dodać odwołanie do biblioteki typów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="27d68-105">To add a reference to a type library in Visual Studio</span></span>  
  
1.  <span data-ttu-id="27d68-106">Zainstaluj plik COM DLL lub EXE na komputerze, chyba, że plik Windows Setup.exe wykonuje instalację.</span><span class="sxs-lookup"><span data-stu-id="27d68-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2.  <span data-ttu-id="27d68-107">Wybierz **projektu**, **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="27d68-107">Choose **Project**, **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="27d68-108">Wybierz w Menedżerze odwołań **COM**.</span><span class="sxs-lookup"><span data-stu-id="27d68-108">In the Reference Manager, choose **COM**.</span></span>  
  
4.  <span data-ttu-id="27d68-109">Wybierz bibliotekę typów, z listy lub Przeglądaj w poszukiwaniu pliku .tlb.</span><span class="sxs-lookup"><span data-stu-id="27d68-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5.  <span data-ttu-id="27d68-110">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="27d68-110">Choose **OK**.</span></span>  
  
6.  <span data-ttu-id="27d68-111">W Eksploratorze rozwiązań Otwórz menu skrótów dla odwołania do właśnie dodane, a następnie wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="27d68-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7.  <span data-ttu-id="27d68-112">W **właściwości** okna, upewnij się, że **Osadź typy współdziałania** właściwość jest ustawiona na **True**.</span><span class="sxs-lookup"><span data-stu-id="27d68-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="27d68-113">To powoduje, że Visual Studio w celu osadzenia informacji o typie dla typów modelu COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="27d68-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27d68-114">Okno dialogowe i menu opcji w oknie mogą się różnić w zależności od wersji programu Visual Studio jest używany.</span><span class="sxs-lookup"><span data-stu-id="27d68-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="27d68-115">Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="27d68-115">To add a reference to a type library for command-line compilation</span></span>  
  
1.  <span data-ttu-id="27d68-116">Generowanie zestawu międzyoperacyjnego, zgodnie z opisem w [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="27d68-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2.  <span data-ttu-id="27d68-117">Użyj [/link (C# opcje kompilatora)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) — opcja kompilatora z nazwą zestawu międzyoperacyjnego do osadzenia informacji o typie dla modelu COM, typy w swoje pliki wykonywalne.</span><span class="sxs-lookup"><span data-stu-id="27d68-117">Use the [/link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [/link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d68-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27d68-118">See also</span></span>
- [<span data-ttu-id="27d68-119">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="27d68-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="27d68-120">Udostępnianie składników COM programowi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="27d68-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="27d68-121">[Przewodnik: Osadzanie informacji o typie z zestawów Microsoft Office](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27d68-121">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies](https://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3(v=vs.100))</span></span>
- [<span data-ttu-id="27d68-122">Przewodnik: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="27d68-122">Walkthrough: Embedding Types from Managed Assemblies</span></span>](https://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)
- [<span data-ttu-id="27d68-123">/ Link (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="27d68-123">/link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="27d68-124">/ Link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27d68-124">/link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
