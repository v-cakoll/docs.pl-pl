---
title: Korzystanie z manipulacji i bezwładności w aplikacjach XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 78deee127f43aac71a1a4daaab808598065c2fe5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741675"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Korzystanie z manipulacji i bezwładności w aplikacjach XNA
W tym artykule opisano, jak można użyć manipulacji i bezwładności przetwarzania w aplikacji Microsoft XNA kontroli przemieszczania figur. Przed przeczytaniem tego artykułu, należy się zapoznać z [omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tematu i należy zapoznać się z XNA podstawowe koncepcje programowania.  
  
 Aby wykonać zadania opisane w tym artykule, musi odwoływać się projektu XNA <xref:System.Windows.Input.Manipulations> zestawu, a musi mieć [Studio gry XNA](http://msdn.microsoft.com/library/bb200104.aspx) ([Pobierz](http://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) zainstalowanej na komputerze tak, że Twoje Projekt można odwoływać się do zestawów XNA.  
  
## <a name="overview-of-functionality"></a>Omówienie funkcji  
 W tym artykule przedstawiono sposób tworzenia niestandardowych klasa, która reprezentuje gier fragment, który korzysta z manipulacji i bezwładności przetwarzania. Ta klasa umożliwia manipulowania gier element na ekranie, przeciągając go za pomocą myszy, a następnie jego zwolnienia. Po wydaniu bezwładności przetwarzania przechowuje element gier, przenoszenie ponieważ stopniowo spowalnia. Ruch jest liniowych i kąta.  
  
 ![Prostej manipulacji i bezwładności aplikacji. ] (../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Ponadto kolekcji niestandardowej jest tworzony, który zarządza wiele figur. Upraszcza to obsługi z klasy gry XNA jest wymagana.  
  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.Manipulations>  
 [Omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
