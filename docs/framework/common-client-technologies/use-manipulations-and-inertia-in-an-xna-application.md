---
title: Korzystanie z manipulacji i bezwładności w aplikacjach XNA
ms.date: 03/30/2017
ms.assetid: b7c18905-850c-4da4-8977-a074406a4263
ms.openlocfilehash: 70b8d0c5c098089b6f16ef817ff86698f68cf7c3
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43478146"
---
# <a name="using-manipulations-and-inertia-in-an-xna-application"></a>Korzystanie z manipulacji i bezwładności w aplikacjach XNA
W tym artykule opisano, jak można użyć manipulacji i bezwładności przetwarzania w aplikacji Microsoft XNA sterowanie ruchem figur. Przed przeczytaniem tego artykułu, należy się zapoznać z [omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md) tematu i należy zapoznać się z XNA podstawowe pojęcia związane z programowaniem.  
  
 Aby wykonać zadania opisane w tym artykule, Twój profil XNA musi odwoływać <xref:System.Windows.Input.Manipulations> zestawie, a także musi mieć [Studio gry XNA](https://msdn.microsoft.com/library/bb200104.aspx) ([Pobierz](https://www.microsoft.com/downloads/details.aspx?FamilyId=7D70D6ED-1EDD-4852-9883-9A33C0AD8FEE&displaylang=en)) zainstalowane na komputerze tak, że Twoje Projekt może odwoływać się zestawów XNA.  
  
## <a name="overview-of-functionality"></a>Omówienie funkcji  
 W tym artykule pokazano, jak utworzyć niestandardowe klasę, która reprezentuje fragment gier, korzystającą z manipulacji i bezwładności przetwarzania. Ta klasa umożliwia Ci manipulowanie gier element na ekranie przez przeciągnięcie go za pomocą myszy, a następnie zwalniając je. Po wydaniu bezwładności przetwarzania przechowuje element gier, stopniowo przeniesienia go spowalnia. Ruch jest liniowych i angular.  
  
 ![Prostej manipulacji i bezwładności aplikacji. ](../../../docs/framework/common-client-technologies/media/ndp-gamexna.jpg "NDP_GameXna")  
  
 Ponadto kolekcji niestandardowej utworzono, która zarządza wieloma figur. Upraszcza to obsługi, która jest wymagana od klasy przeniesienie gry XNA.  
  
 [Tworzenie klasy GamePiece](../../../docs/framework/common-client-technologies/creating-the-gamepiece-class.md)  
  
 [Tworzenie klasy GamePieceCollection](../../../docs/framework/common-client-technologies/creating-the-gamepiececollection-class.md)  
  
 [Tworzenie klasy Game1](../../../docs/framework/common-client-technologies/creating-the-game1-class.md)  
  
 [Listy pełnego kodu](../../../docs/framework/common-client-technologies/full-code-listings.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Input.Manipulations>  
 [Omówienie manipulacji i bezwładności](../../../docs/framework/common-client-technologies/manipulations-and-inertia-overview.md)
