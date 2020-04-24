---
title: Wpływ przestrzeni nazw na rozwijanie odwołań do jednostek w przypadku nowych węzłów zawierających elementy i atrybuty
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
ms.openlocfilehash: 4772e3f7365069c537c4ec3bc8571f2f710bc9fc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710625"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="9f179-102">Wpływ przestrzeni nazw na rozwijanie odwołań do jednostek w przypadku nowych węzłów zawierających elementy i atrybuty</span><span class="sxs-lookup"><span data-stu-id="9f179-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="9f179-103">Ponieważ zawartość deklaracji jednostki może zawierać niemal wszystko, istnieje możliwość, że zawartość może zawierać element, taki jak `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="9f179-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="9f179-104">Gdy plik XML jest analizowany, `&aname;` nie jest rozwinięty wraz z jego zawartością zastępczą podczas analizowania.</span><span class="sxs-lookup"><span data-stu-id="9f179-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="9f179-105">Rozszerzanie kodu XML nie jest wykonywane, ponieważ rozpoznawanie przestrzeni nazw dla elementu nie może wystąpić, dopóki węzeł nie zostanie umieszczony w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="9f179-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="9f179-106">Do tego czasu nie ma informacji o tym, co przestrzeń nazw znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="9f179-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="9f179-107">Gdy węzeł zostanie umieszczony w dokumencie, pojawia się rozpoznawanie przestrzeni nazw, a uzyskana zawartość jednostki jest analizowana do odpowiednich węzłów.</span><span class="sxs-lookup"><span data-stu-id="9f179-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f179-108">Gdy rozszerzenie zostanie wykonane w nowo utworzonym węźle odwołania do jednostki, nigdy nie wystąpi ponownie.</span><span class="sxs-lookup"><span data-stu-id="9f179-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="9f179-109">W związku z tym przestrzenie nazw używane w zamiannym tekście dla elementu są powiązane w chwili, gdy węzeł nadrzędny jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="9f179-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="9f179-110">Można jednak zmienić przestrzeń nazw dla istniejących węzłów odwołań do jednostki, gdy usuniesz i wstawię je w innym miejscu lub w węzłach odwołania do jednostki, które są sklonowane przy użyciu metody **CloneNode** .</span><span class="sxs-lookup"><span data-stu-id="9f179-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f179-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f179-111">See also</span></span>

- [<span data-ttu-id="9f179-112">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="9f179-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
