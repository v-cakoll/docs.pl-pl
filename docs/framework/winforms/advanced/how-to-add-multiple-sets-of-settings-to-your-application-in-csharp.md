---
title: 'Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji wC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 43402d8a1b0b1ca26e656be1424a5fa341ac4728
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57719653"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#
W niektórych przypadkach możesz chcieć mieć wielu zestawów ustawień w aplikacji. Na przykład jeśli tworzysz aplikację, której dana grupa ustawień oczekuje się, zmieniają się często, może być poddanie oddzielić je wszystkie w jednym pliku, dzięki czemu plik można zastąpić hurtowym, pozostawiając inne ustawienia bez zmian. Program Visual Studio umożliwia dodawanie wielu zestawów ustawień do projektu. Dodatkowe zestawy ustawienia są dostępne za pośrednictwem obiektu Properties.Settings.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Aby dodać dodatkowy zestaw ustawień do aplikacji  
  
1.  Z **projektu** menu, wybierz **Dodaj nowy element**. **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku ustawień**, wpisz nazwę pliku, a kliknij **Dodaj** Aby dodać nowy plik ustawień do rozwiązania.  
  
3.  W **Eksploratora rozwiązań**, przeciągnij nowy plik ustawień do **właściwości** folderu. Dzięki temu nowe ustawienia będą dostępne w kodzie.  
  
4.  Dodaj, a następnie użyj ustawień w tym pliku, tak jak każdy inny plik ustawień. Ta grupa ustawień za pomocą obiektu Properties.Settings możesz uzyskać dostęp.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
