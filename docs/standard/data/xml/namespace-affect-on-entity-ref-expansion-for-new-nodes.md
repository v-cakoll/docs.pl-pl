---
title: Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 64359aee-aab0-4042-9a32-d19789af6ca7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4231516848cc50212a3a6a03d101907b2f6b3920
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46561464"
---
# <a name="namespace-affect-on-entity-reference-expansion-for-new-nodes-containing-elements-and-attributes"></a>Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty
Zawartość deklaracji jednostki może zawierać prawie wszystko, istnieje możliwość, który zawartości może zawierać element, takich jak `<!ENTITY aname "<elem>test</elem>">`.  
  
 Gdy zostanie przeanalizowany plik XML, `&aname;` z jego zawartością zastępczy nie jest rozwinięty w czasie analizy. Rozszerzenie pliku XML nie jest wykonywane, ponieważ nie może wystąpić rozpoznawania nazw dla elementu, aż węzeł znajduje się w dokumencie. Do tego czasu nie ma żadnych informacji o jakie przestrzeni nazw znajduje się w zakresie. Gdy węzeł zostanie przełączone do dokumentu, następnie występuje rozpoznawania nazw, a wynikowy jednostki zawartości jest przekształcany do jego odpowiednich węzłów.  
  
> [!NOTE]
>  Gdy wystąpi rozszerzenie w węźle odwołanie do nowo utworzonej jednostki, jej nigdy nie wystąpi ponownie. W związku z tym przestrzenie nazw używane w tekst zastępczy dla elementu są powiązane w czasie, który węzła nadrzędnego jest ustawiony. Jednak przestrzeni nazw można zmienić dla istniejących węzłów odwołanie do jednostki, podczas usuwania i wstawić je w innej lokalizacji lub na węzłach odwołanie do jednostki, które są klonowane z **CloneNode** metody.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
