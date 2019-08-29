---
title: Natywna współdziałanie — .NET
description: Dowiedz się, jak interfejsować ze składnikami macierzystymi w programie .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 3ca213bc7228d2e4337607df2d47b334c5bea14f
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106807"
---
# <a name="native-interoperability"></a>Współdziałanie natywne

W poniższych artykułach przedstawiono różne sposoby wykonywania "natywnych współdziałania" w programie .NET.

Istnieje kilka przyczyn, dla których chcesz wywołać kod natywny:

- Systemy operacyjne korzystają z dużej liczby interfejsów API, które nie znajdują się w zarządzanych bibliotekach klas. Głównym przykładem tego scenariusza będzie dostęp do funkcji zarządzania sprzętem lub systemem operacyjnym.
- Komunikacja z innymi składnikami, które mają lub mogą tworzyć interfejsy ABI w stylu C (natywny interfejsy ABI), takie jak kod Java, który jest udostępniany za pośrednictwem [natywnego interfejsu Java (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) lub dowolnego innego języka zarządzanego, który może generować składnik macierzysty.
- W systemie Windows większość oprogramowania instalowanego, takiego jak pakiet Microsoft Office, rejestruje składniki COM, które reprezentują swoje programy, i umożliwia deweloperom ich automatyzację lub korzystanie z nich. Wymaga to również natywnej współdziałania.

Poprzednia lista nie obejmuje wszystkich potencjalnych sytuacji i scenariuszy, w których deweloper powinien chcieć/lubić, jak ma to być interfejs ze składnikami macierzystymi. Biblioteka klas .NET, na przykład, używa natywnej obsługi współdziałania w celu zaimplementowania uczciwej liczby interfejsów API, takich jak obsługa konsoli i manipulowanie, dostęp do systemu plików i inne. Należy jednak pamiętać, że w razie potrzeby jest dostępna opcja.

> [!NOTE]
> Większość przykładów w tej sekcji zostanie przedstawionych dla wszystkich trzech obsługiwanych platform dla platformy .NET Core (Windows, Linux i macOS). Jednakże w przypadku niektórych krótkich i ilustracyjnych przykładów jest wyświetlany tylko jeden przykład, w którym są używane nazwy i rozszerzenia systemu Windows (czyli "dll" dla bibliotek). Nie oznacza to, że te funkcje nie są dostępne w systemie Linux lub macOS, zostały wykonane tylko w celu wygody.

## <a name="see-also"></a>Zobacz także

- [Wywołanie platformy (P/Invoke)](pinvoke.md)
- [Kierowanie typów](type-marshaling.md)
- [Najlepsze rozwiązania w zakresie współdziałania natywnego](best-practices.md)
