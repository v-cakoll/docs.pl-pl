---
title: Rozwiązywanie problemów z dostawcami typów
description: 'Odkryj rozwiązania potencjalnych problemów, które najprawdopodobniej będzie występować w przypadku użycia dostawcy typów F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f3b8ffdaf615563305b7b84b45a9ed1e066d0dcc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45685689"
---
# <a name="troubleshooting-type-providers"></a>Rozwiązywanie problemów z dostawcami typów

W tym temacie opisano i przewiduje potencjalne rozwiązania problemów, które najprawdopodobniej będzie występować w przypadku użycia dostawcy typów.

## <a name="possible-problems-with-type-providers"></a>Możliwych problemów z dostawcami typów

Jeśli wystąpi problem podczas pracy z dostawcami typów, możesz przejrzeć w poniższej tabeli najbardziej popularne rozwiązania.

|Problem|Sugerowane akcje|
|-------|-----------------|
|**Zmiany schematu**. Typ dostawcy pracy jest najwyższa w przypadku schematu źródła danych jest stabilna. W przypadku dodania danych tabeli lub kolumny lub wprowadzenie innej zmiany do tego schematu, dostawca typów nie rozpoznaje automatycznie tych zmian.|Wyczyść lub ponownie skompilować projekt. Aby wyczyścić projektu, wybierz **kompilacji**, **czysty** *ProjectName* na pasku menu. Aby ponownie skompilować projekt, wybierz opcję **kompilacji**, **odbudować** *ProjectName* na pasku menu. Te akcje zresetowanie wszystkich stanów dostawcy typu i wymuszenie dostawcę Aby ponownie połączyć się ze źródłem danych i uzyskiwanie informacji o schemacie zaktualizowane.|
|**Błąd połączenia**. Adres URL lub ciąg połączenia jest nieprawidłowy, sieć nie działa lub źródła danych lub usługa jest niedostępna.|Usługa sieci web lub usługi OData możesz spróbować adresu URL w przeglądarce Internet Explorer, aby sprawdzić, czy adres URL jest poprawny, a ta usługa jest dostępna. Dla parametrów połączenia bazy danych, można użyć narzędzia połączenia danych w **Eksploratora serwera** Aby sprawdzić, czy parametry połączenia są prawidłowe, a baza danych jest dostępna. Po przywróceniu połączenia należy wyczyścić lub ponownie skompilować projekt, tak aby dostawca typów połączy się ponownie do sieci.|
|**Nieprawidłowe poświadczenia**. Musi mieć prawidłowe uprawnienia do danych źródłowych lub usługi internetowej.|W przypadku połączenia SQL nazwę użytkownika i hasło, które są określone w pliku parametrów lub Konfiguracja połączenia musi być prawidłowy dla bazy danych. Jeśli używasz uwierzytelniania Windows musi mieć dostęp do bazy danych. Administrator bazy danych można określić uprawnienia, czego potrzebujesz, aby uzyskać dostęp do każdej bazy danych i każdego elementu w bazie danych.<br /><br />Usługa sieci web lub usługi danych musi mieć odpowiednie poświadczenia. Większość dostawców typów zapewniają obiektu DataContext, który zawiera właściwość poświadczenia, które można ustawić za pomocą odpowiedniej nazwy użytkownika i klucza dostępu.|
|**Nieprawidłowa ścieżka**. Ścieżka do pliku jest nieprawidłowa.|Sprawdź, czy ścieżka jest poprawna i istnieje plik. Ponadto należy odpowiednio Oferta wszelkie backlashes w ścieżce lub użyj ciąg verbatim lub ciąg potrójnych cudzysłowach.|

## <a name="see-also"></a>Zobacz także

- [Dostawcy typów](index.md)
