---
title: 'Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji wC#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 447d171cf9dbe2672ae138e9e902cbd72a206c94
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969646"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#
W niektórych przypadkach możesz chcieć mieć wielu zestawów ustawień w aplikacji. Na przykład jeśli tworzysz aplikację, której dana grupa ustawień oczekuje się, zmieniają się często, może być poddanie oddzielić je wszystkie w jednym pliku, dzięki czemu plik można zastąpić hurtowym, pozostawiając inne ustawienia bez zmian. Program Visual Studio umożliwia dodawanie wielu zestawów ustawień do projektu. Dodatkowe zestawy ustawienia są dostępne za pośrednictwem obiektu Properties.Settings.  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>Aby dodać dodatkowy zestaw ustawień do aplikacji  
  
1.  Z **projektu** menu, wybierz **Dodaj nowy element**. **Dodaj nowy element** zostanie otwarte okno dialogowe.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **pliku ustawień**, wpisz nazwę pliku, a kliknij **Dodaj** Aby dodać nowy plik ustawień do rozwiązania.  
  
3.  W **Eksploratora rozwiązań**, przeciągnij nowy plik ustawień do **właściwości** folderu. Dzięki temu nowe ustawienia będą dostępne w kodzie.  
  
4.  Dodaj, a następnie użyj ustawień w tym pliku, tak jak każdy inny plik ustawień. Ta grupa ustawień za pomocą obiektu Properties.Settings możesz uzyskać dostęp.  
  
## <a name="see-also"></a>Zobacz także
- [Używanie ustawień aplikacji i ustawień użytkownika](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
