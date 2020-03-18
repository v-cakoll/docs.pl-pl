---
title: Natywna interoperacyjność - .NET
description: Dowiedz się, jak współpracować ze składnikami macierzystymi w platformie .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706338"
---
# <a name="native-interoperability"></a>Współdziałanie natywne

W poniższych artykułach przedstawiono różne sposoby wykonywania "natywnej interoperacyjności" w .NET.

Istnieje kilka powodów, dla których chcesz wywołać kod macierzysty:

- Systemy operacyjne są wyposażone w dużą liczbę interfejsów API, które nie są obecne w bibliotekach klas zarządzanych. Najlepszym przykładem dla tego scenariusza będzie dostęp do funkcji zarządzania sprzętem lub systemem operacyjnym.
- Komunikowanie się z innymi składnikami, które mają lub mogą tworzyć afi w stylu C (natywne afi), takich jak kod Java, który jest udostępniane za pośrednictwem [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub innego języka zarządzanego, który może produkować składnik macierzystych.
- W systemie Windows większość oprogramowania, które zostanie zainstalowane, na przykład pakietu Microsoft Office, rejestruje składniki COM, które reprezentują ich programy i umożliwiają deweloperom ich automatyzację lub korzystanie z nich. Wymaga to również natywnej interoperacyjności.

Poprzednia lista nie obejmuje wszystkich potencjalnych sytuacji i scenariuszy, w których deweloper chciałby/like/need do interfejsu ze składnikami macierzystymi. Na przykład biblioteka klas .NET używa natywnej obsługi współdziałania do zaimplementowania sporej liczby interfejsów API, takich jak obsługa konsoli i manipulacja, dostęp do systemu plików i inne. Jednak ważne jest, aby pamiętać, że istnieje opcja w razie potrzeby.

> [!NOTE]
> Większość przykładów w tej sekcji zostanie przedstawiona dla wszystkich trzech obsługiwanych platform dla .NET Core (Windows, Linux i macOS). Jednak w przypadku niektórych krótkich i ilustrujących przykładów wyświetlany jest tylko jeden przykład, który używa nazw plików i rozszerzeń systemu Windows (czyli "dll" dla bibliotek). Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, zostało to zrobione tylko dla wygody.

## <a name="see-also"></a>Zobacz też

- [Wywołanie platformy (P/Invoke)](pinvoke.md)
- [Marshaling typów](type-marshaling.md)
- [Natywne najlepsze praktyki w zakresie interoperacyjności](best-practices.md)
