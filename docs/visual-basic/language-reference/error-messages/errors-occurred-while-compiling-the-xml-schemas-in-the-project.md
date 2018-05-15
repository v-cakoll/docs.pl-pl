---
title: Wystąpiły błędy podczas kompilowania schematów XML w projekcie
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 0cc565809792c619ca9903f9ef9b029b51a8aa17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="a0d14-102">Wystąpiły błędy podczas kompilowania schematów XML w projekcie</span><span class="sxs-lookup"><span data-stu-id="a0d14-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="a0d14-103">Wystąpiły błędy podczas kompilowania schematów XML w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a0d14-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="a0d14-104">Z tego powodu narzędzie IntelliSense XML nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="a0d14-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="a0d14-105">Istnieje błąd w schemacie definicji schematu XML (XSD) dołączony do projektu.</span><span class="sxs-lookup"><span data-stu-id="a0d14-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="a0d14-106">Ten błąd występuje, gdy dodać plik schematu (XSD) XSD, który powoduje konflikt z istniejącą schematu XSD ustawiony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a0d14-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="a0d14-107">**Identyfikator błędu:** BC36810</span><span class="sxs-lookup"><span data-stu-id="a0d14-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a0d14-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="a0d14-108">To correct this error</span></span>  
  
-   <span data-ttu-id="a0d14-109">Kliknij dwukrotnie ikonę ostrzeżenia w **listy błędów** okna.</span><span class="sxs-lookup"><span data-stu-id="a0d14-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="a0d14-110">Visual Basic spowoduje przejście do lokalizacji określonej w pliku XSD, który jest źródłem ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="a0d14-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="a0d14-111">Napraw błąd w schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="a0d14-111">Correct the error in the XSD schema.</span></span>  
  
-   <span data-ttu-id="a0d14-112">Upewnij się, że wszystkie wymagane pliki XSD schematu (.xsd) znajdują się w projekcie.</span><span class="sxs-lookup"><span data-stu-id="a0d14-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="a0d14-113">Może zajść potrzeba kliknięcia przycisku **Pokaż wszystkie pliki** na **projektu** menu, aby zobaczyć XSD Twoje pliki w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="a0d14-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="a0d14-114">Kliknij prawym przyciskiem myszy plik XSD, a następnie kliknij przycisk **załącz do projektu** Aby dołączyć plik do projektu.</span><span class="sxs-lookup"><span data-stu-id="a0d14-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
-   <span data-ttu-id="a0d14-115">Jeśli używasz XML do kreatora schematu, ten błąd może wystąpić, jeśli wnioskować więcej niż jeden raz schematów z tego samego źródła.</span><span class="sxs-lookup"><span data-stu-id="a0d14-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="a0d14-116">W takim przypadku możesz usunąć istniejące pliki schematu XSD z projektu, Dodaj nowe XML do schematu szablonu elementu, a następnie podaj XML do kreatora schematu ze wszystkich odpowiednich źródłami XML dla projektu.</span><span class="sxs-lookup"><span data-stu-id="a0d14-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
-   <span data-ttu-id="a0d14-117">Jeśli błąd nie zostanie zidentyfikowana w schematu XSD, kompilator XML może nie mieć wystarczającej ilości informacji zapewnienie szczegółowy komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="a0d14-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="a0d14-118">Dzięki temu można uzyskać bardziej szczegółowe informacje o błędzie, jeśli upewnij się, że przestrzenie nazw XML dla plików XSD zawarte w Twojej dopasowania projektu przestrzeni nazw XML dla schematu XML w Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0d14-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0d14-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0d14-119">See Also</span></span>  
 [<span data-ttu-id="a0d14-120">Okno listy błędów</span><span class="sxs-lookup"><span data-stu-id="a0d14-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)  
 [<span data-ttu-id="a0d14-121">XML</span><span class="sxs-lookup"><span data-stu-id="a0d14-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
