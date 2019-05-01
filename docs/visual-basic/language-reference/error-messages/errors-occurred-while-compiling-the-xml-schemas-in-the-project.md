---
title: Wystąpiły błędy podczas kompilowania schematów XML w projekcie
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803288"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a><span data-ttu-id="f7816-102">Wystąpiły błędy podczas kompilowania schematów XML w projekcie</span><span class="sxs-lookup"><span data-stu-id="f7816-102">Errors occurred while compiling the XML schemas in the project</span></span>
<span data-ttu-id="f7816-103">Wystąpiły błędy podczas kompilowania schematów XML w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f7816-103">Errors occurred while compiling the XML schemas in the project.</span></span> <span data-ttu-id="f7816-104">W związku z tym funkcji IntelliSense XML nie jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="f7816-104">Because of this, XML IntelliSense is not available.</span></span>  
  
 <span data-ttu-id="f7816-105">Istnieje błąd w schemacie definicji schematu XML (XSD), zawarty w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f7816-105">There is an error in an XML Schema Definition (XSD) schema included in the project.</span></span> <span data-ttu-id="f7816-106">Ten błąd występuje, gdy dodasz plik XSD schematu (XSD), który powoduje konflikt z istniejącego schematu XSD ustawiony dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f7816-106">This error occurs when you add an XSD schema (.xsd) file that conflicts with the existing XSD schema set for the project.</span></span>  
  
 <span data-ttu-id="f7816-107">**Identyfikator błędu:** BC36810</span><span class="sxs-lookup"><span data-stu-id="f7816-107">**Error ID:** BC36810</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7816-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="f7816-108">To correct this error</span></span>  
  
- <span data-ttu-id="f7816-109">Kliknij dwukrotnie ikonę ostrzeżenia w **listy błędów** okna.</span><span class="sxs-lookup"><span data-stu-id="f7816-109">Double-click the warning in the **Errors List** window.</span></span> <span data-ttu-id="f7816-110">Visual Basic spowoduje przejście do lokalizacji w pliku XSD, który jest źródłem ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="f7816-110">Visual Basic will take you to the location in the XSD file that is the source of the warning.</span></span> <span data-ttu-id="f7816-111">Popraw błąd w schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="f7816-111">Correct the error in the XSD schema.</span></span>  
  
- <span data-ttu-id="f7816-112">Upewnij się, że wszystkie wymagane pliki schematów (XSD) XSD znajdują się w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f7816-112">Ensure that all required XSD schema (.xsd) files are included in the project.</span></span> <span data-ttu-id="f7816-113">Może być konieczne kliknięcie **Pokaż wszystkie pliki** na **projektu** menu, aby wyświetlić swoje XSD pliki **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f7816-113">You may need to click **Show All Files** on the **Project** menu to see your .xsd files in **Solution Explorer**.</span></span> <span data-ttu-id="f7816-114">Kliknij prawym przyciskiem myszy plik XSD, a następnie kliknij przycisk **załącz do projektu** dołączenie pliku w projekcie.</span><span class="sxs-lookup"><span data-stu-id="f7816-114">Right-click an .xsd file and then click **Include In Project** to include the file in your project.</span></span>  
  
- <span data-ttu-id="f7816-115">Jeśli używasz XML do kreatora schematu, ten błąd może wystąpić, jeśli wywnioskować więcej niż jeden raz schematów z tego samego źródła.</span><span class="sxs-lookup"><span data-stu-id="f7816-115">If you are using the XML to Schema Wizard, this error can occur if you infer schemas more than one time from the same source.</span></span> <span data-ttu-id="f7816-116">W takim przypadku możesz usunąć istniejące pliki schematu XSD z projektu, dodać nowe XML do schematu szablonu elementu, a następnie podaj plik XML do kreatora schematu za pomocą wszystkich odpowiednich źródeł XML dla projektu.</span><span class="sxs-lookup"><span data-stu-id="f7816-116">In this case, you can remove the existing XSD schema files from the project, add a new XML to Schema item template, and then provide the XML to Schema Wizard with all the applicable XML sources for your project.</span></span>  
  
- <span data-ttu-id="f7816-117">Jeśli żaden błąd nie zostanie zidentyfikowana w schemacie XSD, kompilator XML może nie mieć wystarczających informacji, aby zapewnić szczegółowy komunikat o błędzie.</span><span class="sxs-lookup"><span data-stu-id="f7816-117">If no error is identified in your XSD schema, the XML compiler may not have enough information to provide a detailed error message.</span></span> <span data-ttu-id="f7816-118">Dzięki temu można uzyskać bardziej szczegółowe informacje o błędzie, jeśli należy zapewnić, że obszary nazw XML dotyczących XSD plików zawarte w rozgrywki projektu przestrzeni nazw XML dla schematu XML w Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7816-118">You may be able to get more detailed error information if you ensure that the XML namespaces for the .xsd files included in your project match the XML namespaces identified for the XML Schema set in Visual Studio.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7816-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f7816-119">See also</span></span>

- [<span data-ttu-id="f7816-120">Okno listy błędów</span><span class="sxs-lookup"><span data-stu-id="f7816-120">Error List Window</span></span>](/visualstudio/ide/reference/error-list-window)
- [<span data-ttu-id="f7816-121">XML</span><span class="sxs-lookup"><span data-stu-id="f7816-121">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
