---
title: Współdziałanie natywne — .NET
description: Dowiedz się, jak współpracować z usługą składnikami macierzystymi na platformie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: b01ea9c17db6da32755309d9c1c2359cecaa1155
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062714"
---
# <a name="native-interoperability"></a>Współdziałanie natywne

Następujące artykuły pokazują różne sposoby wykonywania "interoperacyjności macierzystej" na platformie .NET.

Istnieje kilka powodów dlaczego warto mogą wywoływać kodu natywnego:

* Systemy operacyjne są dostarczane z dużą liczbą interfejsów API, które nie są obecne w bibliotekach klas zarządzanych. Podstawowy przykład w tym scenariuszu będzie dostęp do sprzętu lub systemu operacyjnego, funkcji zarządzania.
* Podczas komunikowania się z innymi składnikami, które lub może tworzyć interfejsy ABI stylu języka C (natywnych interfejsów ABI), takie jak kod Java, który jest uwidaczniany za pomocą [interfejsem Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnym innym języku zarządzanych, które może powodować składnika macierzystego.
* W Windows większość oprogramowania instalowanego, takich jak pakiet Microsoft Office rejestruje składników COM, które reprezentują swoich programów i umożliwiają deweloperom Automatyzowanie je lub używać ich. Wymaga to interoperacyjności macierzystej.

Poprzedniej liście nie obejmuje wszystkich potencjalnych sytuacji i scenariusze, w których deweloper może chcesz/podobne/potrzebę do połączenia interfejsem z składnikami macierzystymi. Biblioteka klas programu .NET, na przykład korzysta z obsługi interoperacyjności macierzystej zaimplementować podejście liczbę interfejsów API, takich jak obsługa konsoli i manipulowania, dostęp do systemu plików i inne. Jest jednak należy pamiętać, że jest dostępna opcja w razie potrzeby.

> [!NOTE]
> Większość przykładów w tej sekcji zostaną przedstawione na potrzeby wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS). Kilka przykładów krótki i opisowy tylko jeden przykład jest jednak wyświetlany korzystający Windows nazwy plików i rozszerzenia (czyli "dll" jak biblioteki). Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, została wykonana jedynie dla wygody sake.

## <a name="see-also"></a>Zobacz także

- [Wywołanie platformy (P/Invoke)](pinvoke.md)
- [Marshaling typów](type-marshaling.md)
- [Współdziałanie natywne najlepszych rozwiązań](best-practices.md)
