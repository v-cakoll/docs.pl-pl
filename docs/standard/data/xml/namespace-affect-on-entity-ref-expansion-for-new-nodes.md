---
title: Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44216428"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a><span data-ttu-id="ed964-102">Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty</span><span class="sxs-lookup"><span data-stu-id="ed964-102">Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes</span></span>
<span data-ttu-id="ed964-103">Zawartość deklaracji jednostki może zawierać prawie wszystko, istnieje możliwość, który zawartości może zawierać element, takich jak `<!ENTITY aname "<elem>test</elem>">`.</span><span class="sxs-lookup"><span data-stu-id="ed964-103">Because the content of an entity declaration can contain almost anything, there is a possibility that the content could contain an element like `<!ENTITY aname "<elem>test</elem>">`.</span></span>  
  
 <span data-ttu-id="ed964-104">Gdy zostanie przeanalizowany plik XML, `&aname;` z jego zawartością zastępczy nie jest rozwinięty w czasie analizy.</span><span class="sxs-lookup"><span data-stu-id="ed964-104">When the XML is parsed, `&aname;` is not expanded with its replacement content at parse time.</span></span> <span data-ttu-id="ed964-105">Rozszerzenie pliku XML nie jest wykonywane, ponieważ nie może wystąpić rozpoznawania nazw dla elementu, aż węzeł znajduje się w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="ed964-105">The expansion of the XML is not done because resolution of the namespace for the element cannot occur until the node is placed in the document.</span></span> <span data-ttu-id="ed964-106">Do tego czasu nie ma żadnych informacji o jakie przestrzeni nazw znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="ed964-106">Until that time, there is no knowledge of what namespace is in scope.</span></span> <span data-ttu-id="ed964-107">Gdy węzeł zostanie przełączone do dokumentu, następnie występuje rozpoznawania nazw, a wynikowy jednostki zawartości jest przekształcany do jego odpowiednich węzłów.</span><span class="sxs-lookup"><span data-stu-id="ed964-107">When the node is put into the document, then the namespace resolution occurs, and the resulting entity content is parsed into its appropriate nodes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ed964-108">Gdy wystąpi rozszerzenie w węźle odwołanie do nowo utworzonej jednostki, jej nigdy nie wystąpi ponownie.</span><span class="sxs-lookup"><span data-stu-id="ed964-108">Once the expansion occurs on a newly created entity reference node, it never reoccurs.</span></span> <span data-ttu-id="ed964-109">W związku z tym przestrzenie nazw używane w tekst zastępczy dla elementu są powiązane w czasie, który węzła nadrzędnego jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="ed964-109">Therefore, the namespaces used in the replacement text for the element are bound at the time that the parent node is set.</span></span> <span data-ttu-id="ed964-110">Jednak przestrzeni nazw można zmienić dla istniejących węzłów odwołanie do jednostki, podczas usuwania i wstawić je w innej lokalizacji lub na węzłach odwołanie do jednostki, które są klonowane z **CloneNode** metody.</span><span class="sxs-lookup"><span data-stu-id="ed964-110">However, the namespace can be changed for existing entity reference nodes when you remove and insert them somewhere else, or on entity reference nodes that are cloned with the **CloneNode** method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed964-111">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed964-111">See also</span></span>

- [<span data-ttu-id="ed964-112">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="ed964-112">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
