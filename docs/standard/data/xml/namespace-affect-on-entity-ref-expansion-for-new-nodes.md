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
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Wpływ przestrzeni nazw na rozwijanie odwołań do jednostek w przypadku nowych węzłów zawierających elementy i atrybuty
Ponieważ zawartość deklaracji jednostki może zawierać niemal wszystko, istnieje możliwość, że zawartość może zawierać element, taki jak `<!ENTITY aname "<elem>test</elem>">`.  
  
 Po przeanalizowaniu kodu XML `&aname;` nie jest rozwinięty wraz z jego zawartością zastępczą podczas analizowania. Rozszerzanie kodu XML nie jest wykonywane, ponieważ rozpoznawanie przestrzeni nazw dla elementu nie może wystąpić, dopóki węzeł nie zostanie umieszczony w dokumencie. Do tego czasu nie ma informacji o tym, co przestrzeń nazw znajduje się w zakresie. Gdy węzeł zostanie umieszczony w dokumencie, pojawia się rozpoznawanie przestrzeni nazw, a uzyskana zawartość jednostki jest analizowana do odpowiednich węzłów.  
  
> [!NOTE]
> Gdy rozszerzenie zostanie wykonane w nowo utworzonym węźle odwołania do jednostki, nigdy nie wystąpi ponownie. W związku z tym przestrzenie nazw używane w zamiannym tekście dla elementu są powiązane w chwili, gdy węzeł nadrzędny jest ustawiony. Można jednak zmienić przestrzeń nazw dla istniejących węzłów odwołań do jednostki, gdy usuniesz i wstawię je w innym miejscu lub w węzłach odwołania do jednostki, które są sklonowane przy użyciu metody **CloneNode** .  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
