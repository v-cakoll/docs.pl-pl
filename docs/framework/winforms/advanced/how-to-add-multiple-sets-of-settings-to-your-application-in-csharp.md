---
title: 'Porady: dodawanie wielu zestawów ustawień do aplikacji w C#'
description: Dowiedz się, jak dodać wiele zestawów ustawień Windows Forms do aplikacji w języku C# za pomocą programu Visual Studio.
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 579374ff101758b3224bc122c46b891280ed2609
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173448"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>Instrukcje: Dodawanie wielu zestawów ustawień do aplikacji w języku C\#

W niektórych przypadkach może być konieczne posiadanie wielu zestawów ustawień w aplikacji. Na przykład w przypadku tworzenia aplikacji, w której oczekiwana jest zmiana konkretnej grupy ustawień, warto oddzielić je wszystkie w jednym pliku, aby można było wymienić ten plik, pozostawiając inne ustawienia bez zmian. Program Visual Studio umożliwia dodanie wielu zestawów ustawień do projektu. Dostęp do dodatkowych zestawów ustawień można uzyskać za pośrednictwem `Properties.Settings` obiektu.

## <a name="add-an-additional-set-of-settings"></a>Dodaj dodatkowy zestaw ustawień

1. W programie Visual Studio w menu **projekt** wybierz polecenie **Dodaj nowy element**.

   Zostanie otwarte okno dialogowe **Dodaj nowy element** .

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **plik ustawień**, wprowadź nazwę pliku, a następnie kliknij przycisk **Dodaj** , aby dodać nowy plik ustawień do rozwiązania.

3. W **Eksplorator rozwiązań**przeciągnij nowy plik ustawień do folderu **Właściwości** . Dzięki temu nowe ustawienia będą dostępne w kodzie.

4. Dodaj i Użyj ustawień w tym pliku, tak jak każdy inny plik ustawień. Możesz uzyskać dostęp do tej grupy ustawień za pośrednictwem `Properties.Settings` obiektu.

## <a name="see-also"></a>Zobacz też

- [Używanie ustawień aplikacji i ustawień użytkownika](using-application-settings-and-user-settings.md)
- [Przegląd ustawień aplikacji](application-settings-overview.md)
