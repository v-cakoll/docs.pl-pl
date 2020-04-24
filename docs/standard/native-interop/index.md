---
title: Natywna współdziałanie — .NET
description: Dowiedz się, jak interfejsować ze składnikami macierzystymi w programie .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 330466d74cc268214f74c4f575e6a2961f678972
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75706338"
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

## <a name="see-also"></a>Zobacz też

- [Wywołanie platformy (P/Invoke)](pinvoke.md)
- [Marshaling typów](type-marshaling.md)
- [Najlepsze rozwiązania w zakresie współdziałania natywnego](best-practices.md)
