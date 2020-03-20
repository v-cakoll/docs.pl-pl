---
title: 'Porady: dodawanie odwołań do bibliotek typów'
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- interop assemblies, generating
- type libraries
- COM interop, importing type library
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
ms.openlocfilehash: 1e82a499b77cc6d1d49eaf13e243201bbdc4c5fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181442"
---
# <a name="how-to-add-references-to-type-libraries"></a><span data-ttu-id="1d101-102">Porady: dodawanie odwołań do bibliotek typów</span><span class="sxs-lookup"><span data-stu-id="1d101-102">How to: Add References to Type Libraries</span></span>
<span data-ttu-id="1d101-103">Visual Studio generuje zestaw interop zawierający metadane podczas dodawania odwołania do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="1d101-103">Visual Studio generates an interop assembly containing metadata when you add a reference to a type library.</span></span> <span data-ttu-id="1d101-104">Jeśli podstawowy zestaw międzyoperacyjny jest dostępny, Visual Studio używa istniejącego zestawu przed wygenerowaniem nowego zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="1d101-104">If a primary interop assembly is available, Visual Studio uses the existing assembly before generating a new interop assembly.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-in-visual-studio"></a><span data-ttu-id="1d101-105">Aby dodać odwołanie do biblioteki typów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d101-105">To add a reference to a type library in Visual Studio</span></span>  
  
1. <span data-ttu-id="1d101-106">Zainstaluj plik BIBLIOTEKI DLL lub EXE COM na komputerze, chyba że plik Setup.exe systemu Windows wykona instalację.</span><span class="sxs-lookup"><span data-stu-id="1d101-106">Install the COM DLL or EXE file on your computer, unless a Windows Setup.exe file performs the installation for you.</span></span>  
  
2. <span data-ttu-id="1d101-107">Wybierz **polecenie Projekt**, Dodaj **odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="1d101-107">Choose **Project**, **Add Reference**.</span></span>  
  
3. <span data-ttu-id="1d101-108">W Menedżerze odwołań wybierz pozycję **COM**.</span><span class="sxs-lookup"><span data-stu-id="1d101-108">In the Reference Manager, choose **COM**.</span></span>  
  
4. <span data-ttu-id="1d101-109">Wybierz bibliotekę typów z listy lub wyszukaj plik .tlb.</span><span class="sxs-lookup"><span data-stu-id="1d101-109">Select the type library from the list, or browse for the .tlb file.</span></span>  
  
5. <span data-ttu-id="1d101-110">Wybierz pozycję **OK**.</span><span class="sxs-lookup"><span data-stu-id="1d101-110">Choose **OK**.</span></span>  
  
6. <span data-ttu-id="1d101-111">W Eksploratorze rozwiązań otwórz menu skrótów dla właśnie dodanego odniesienia, a następnie wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="1d101-111">In Solution Explorer, open the shortcut menu for the reference you just added, and then choose **Properties**.</span></span>  
  
7. <span data-ttu-id="1d101-112">W oknie **Właściwości** upewnij się, że właściwość **Osadzanie typów międzyop jest** ustawiona na **Wartość True**.</span><span class="sxs-lookup"><span data-stu-id="1d101-112">In the **Properties** window, make sure that the **Embed Interop Types** property is set to **True**.</span></span> <span data-ttu-id="1d101-113">Powoduje to, że program Visual Studio osadza informacje o typie dla typów COM w plikach wykonywalnych, eliminując konieczność wdrażania podstawowych zestawów międzyoperacyjnych za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1d101-113">This causes Visual Studio to embed type information for COM types in your executables, eliminating the need to deploy primary interop assemblies with your app.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d101-114">Opcje menu i okna dialogowego mogą się różnić w zależności od używanej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1d101-114">The menu and dialog box options may vary depending on the version of Visual Studio you're using.</span></span>  
  
### <a name="to-add-a-reference-to-a-type-library-for-command-line-compilation"></a><span data-ttu-id="1d101-115">Aby dodać odwołanie do biblioteki typów dla kompilacji wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1d101-115">To add a reference to a type library for command-line compilation</span></span>  
  
1. <span data-ttu-id="1d101-116">Generowanie zestawu międzyoperacyjnego zgodnie z opisem w [jak: Generowanie zestawów międzyoperacyjnych z bibliotek typów](how-to-generate-interop-assemblies-from-type-libraries.md).</span><span class="sxs-lookup"><span data-stu-id="1d101-116">Generate an interop assembly as described in [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>  
  
2. <span data-ttu-id="1d101-117">Użyj opcji [kompilatora -link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) lub [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) o nazwie zestawu interop, aby osadzić informacje o typie dla typów COM w plikach wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="1d101-117">Use the [-link (C# Compiler Options)](../../csharp/language-reference/compiler-options/link-compiler-option.md) or [-link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) compiler option with the interop assembly name to embed type information for COM types in your executables.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d101-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d101-118">See also</span></span>

- [<span data-ttu-id="1d101-119">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="1d101-119">Importing a Type Library as an Assembly</span></span>](importing-a-type-library-as-an-assembly.md)
- [<span data-ttu-id="1d101-120">Udostępnianie składników COM programowi.NET Framework</span><span class="sxs-lookup"><span data-stu-id="1d101-120">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- [<span data-ttu-id="1d101-121">Przewodnik: osadzanie typów z zarządzanych zestawów w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1d101-121">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio</span></span>](../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="1d101-122">-link (Opcje kompilatora języka C#)</span><span class="sxs-lookup"><span data-stu-id="1d101-122">-link (C# Compiler Options)</span></span>](../../csharp/language-reference/compiler-options/link-compiler-option.md)
- [<span data-ttu-id="1d101-123">-link (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d101-123">-link (Visual Basic)</span></span>](../../visual-basic/reference/command-line-compiler/link.md)
