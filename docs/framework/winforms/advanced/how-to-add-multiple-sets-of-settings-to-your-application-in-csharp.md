---
title: 'Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w C#'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: c6842d11c04e905d42734af939f2c3f0cfeacd47
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040123"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#

W niektórych przypadkach może być konieczne posiadanie wielu zestawów ustawień w aplikacji. Na przykład w przypadku tworzenia aplikacji, w której oczekiwana jest zmiana konkretnej grupy ustawień, warto oddzielić je wszystkie w jednym pliku, aby można było wymienić ten plik, pozostawiając inne ustawienia bez zmian. Program Visual Studio umożliwia dodanie wielu zestawów ustawień do projektu. Dostęp do dodatkowych zestawów ustawień można uzyskać za pośrednictwem `Properties.Settings` obiektu.

## <a name="add-an-additional-set-of-settings"></a>Dodaj dodatkowy zestaw ustawień

1. W programie Visual Studio w menu **projekt** wybierz polecenie **Dodaj nowy element**.

   **Dodaj nowy element** zostanie otwarte okno dialogowe.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik ustawień**, wprowadź nazwę pliku, a następnie kliknij przycisk **Dodaj** , aby dodać nowy plik ustawień do rozwiązania.

3. W **Eksplorator rozwiązań**przeciągnij nowy plik ustawień do folderu **Właściwości** . Dzięki temu nowe ustawienia będą dostępne w kodzie.

4. Dodaj i Użyj ustawień w tym pliku, tak jak każdy inny plik ustawień. Możesz uzyskać dostęp do tej grupy ustawień za pośrednictwem `Properties.Settings` obiektu.

## <a name="see-also"></a>Zobacz także

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
