---
title: Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu
ms.date: 03/30/2017
helpviewer_keywords:
- code security, unmanaged code
- unmanaged code, securing
- security [.NET Framework], unmanaged code
- secure coding, unmanaged code
ms.assetid: a8d15139-d368-4c9c-a747-ba757781117c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec97861a9d748767199da3e1fb7f53361c3a48ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966122"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu
Kod biblioteki musi być wywoływany w kodzie niezarządzanym (na przykład interfejsy API kodu natywnego, takie jak Win32). Ponieważ oznacza to przechodzenie poza obwód zabezpieczeń dla kodu zarządzanego, wymagane jest zachowanie ostrożności. Jeśli kod jest neutralny pod względem zabezpieczeń, zarówno kod, jak i kod, który wywołuje ten element musi mieć uprawnienia<xref:System.Security.Permissions.SecurityPermission> <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> do kodu niezarządzanego (z określoną flagą).  
  
 Jednak często jest to nieuzasadnione, aby obiekt wywołujący miał takie zaawansowane uprawnienia. W takich przypadkach zaufany kod może być przechodzeniem między elementami, podobnymi do zarządzanej otoki lub kodu biblioteki opisanym w artykule [Zabezpieczanie kodu otoki](../../../docs/framework/misc/securing-wrapper-code.md). Jeśli podstawowa funkcja kodu niezarządzanego jest całkowicie bezpieczna, można ją bezpośrednio uwidocznić; w przeciwnym razie najpierw wymagane jest odpowiednie sprawdzenie uprawnień (żądanie).  
  
 Gdy kod wywołuje się w niezarządzanym kodzie, ale nie chcesz wymagać od wywołujących uprawnień dostępu do niezarządzanego kodu, musisz pomusić to prawo. Potwierdzenie blokuje stos w ramce. Należy zachować ostrożność, aby w tym procesie nie utworzyć otworu zabezpieczeń. Zazwyczaj oznacza to, że należy zażądać odpowiednich uprawnień dla obiektów wywołujących, a następnie użyć kodu niezarządzanego do wykonania tylko tego, co zezwala na to uprawnienie i nie tylko. W niektórych przypadkach (na przykład funkcja Get of Day) kod niezarządzany może być bezpośrednio narażony na wywołujących bez żadnych kontroli zabezpieczeń. W każdym przypadku każdy kod, który potwierdza, musi być odpowiedzialny za zabezpieczenia.  
  
 Ponieważ kod zarządzany, który zapewnia ścieżkę kodu do kodu natywnego, jest potencjalnym celem złośliwego kodu, co określa, który kod niezarządzany może być bezpiecznie używany i jak musi być używany, wymaga najwyższej staranności. Ogólnie rzecz biorąc, kod niezarządzany nigdy nie powinien być bezpośrednio narażony na częściowo zaufane obiekty wywołujące. Istnieją dwa podstawowe zagadnienia dotyczące oceny bezpieczeństwa niezarządzanego kodu w bibliotekach, które są wywoływane za pomocą częściowo zaufanego kodu:  
  
- **Funkcja**. Czy niezarządzany interfejs API udostępnia funkcje, które nie zezwalają wywołującym na wykonywanie potencjalnie niebezpiecznych operacji? Zabezpieczenia dostępu kodu używają uprawnień, aby wymusić dostęp do zasobów, dlatego należy rozważyć, czy interfejs API używa plików, interfejsu użytkownika lub wątków, czy udostępnia chronione informacje. W takim przypadku kod zarządzany musi wymagać wymaganych uprawnień przed zezwoleniem na jego wprowadzenie. Ponadto, chociaż nie jest chroniony przez uprawnienie, dostęp do pamięci musi być ograniczony do rygorystycznego bezpieczeństwa typów.  
  
- **Sprawdzanie parametrów**. Typowy atak polega na przejęciu nieoczekiwanych parametrów do wbudowanych metod interfejsu API kodu niezarządzanego w wyniku próby ich przeprowadzenia poza specyfikacją. Przepełnienia buforów przy użyciu indeksu out-of-Range lub wartości przesunięcia to jeden typowy przykład tego typu ataku, jak wszystkie parametry, które mogą wykorzystać usterkę w kodzie źródłowym. W takim przypadku, nawet jeśli interfejs API kodu niezarządzanego jest funkcjonalnie bezpieczny (po wymaganym zapotrzebowaniu) dla częściowo zaufanych obiektów wywołujących, kod zarządzany musi również sprawdzać ważność parametrów, aby upewnić się, że żadne nieprzewidziane wywołania nie są możliwe przed złośliwym kodem przy użyciu zarządzanego warstwa otoki kodu.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Korzystanie z SuppressUnmanagedCodeSecurityAttribute  
 Istnieje aspekt wydajności służący do potwierdzania, a następnie wywoływania kodu niezarządzanego. Dla każdego takiego wywołania system zabezpieczeń automatycznie wymaga uprawnień do kodu niezarządzanego, co spowoduje, że każdy z nich jest przeszukiwany przez stos. Jeśli postanowisz i natychmiast wywołasz kod niezarządzany, przeszukiwanie stosu może być bez znaczenia: składa się z potwierdzenia i niezarządzanego wywołania kodu.  
  
 Atrybut niestandardowy o nazwie <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> można zastosować do punktów wejścia kodu niezarządzanego, aby wyłączyć normalne sprawdzanie zabezpieczeń, <xref:System.Security.Permissions.SecurityPermission> które wymaga <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określonego uprawnienia. W tym celu należy zawsze wykonać wyjątkową ostrożność, ponieważ ta akcja tworzy otwarte drzwi w niezarządzanym kodzie bez sprawdzania zabezpieczeń środowiska uruchomieniowego. Należy zauważyć, że nawet w przypadku zastosowania **SuppressUnmanagedCodeSecurityAttribute** istnieje jednorazowe sprawdzenie zabezpieczeń, które odbywa się w kompilacji just-in-Time (JIT), aby upewnić się, że bezpośredni obiekt wywołujący ma uprawnienia do wywoływania kodu niezarządzanego.  
  
 Jeśli używasz **SuppressUnmanagedCodeSecurityAttribute**, sprawdź następujące kwestie:  
  
- Ustaw niezarządzany punkt wejścia kodu wewnętrznie lub w inny sposób niedostępny poza kodem.  
  
- Wszelkie wywołania w kodzie niezarządzanym to potencjalna Luka w zabezpieczeniach. Upewnij się, że Twój kod nie jest portalem złośliwego kodu do pośredniego wywołania kodu niezarządzanego i uniknięcia kontroli zabezpieczeń. Uprawnienia na żądanie, jeśli jest to konieczne.  
  
- Użyj konwencji nazewnictwa, aby jawnie określić, kiedy tworzysz niebezpieczną ścieżkę do kodu niezarządzanego, zgodnie z opisem w sekcji poniżej.  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Konwencja nazewnictwa dla metod kodu niezarządzanego  
 Do nazewnictwa metod kodu niezarządzanego zostały ustanowione użyteczne i zdecydowanie zalecane konwencje. Wszystkie metody kodu niezarządzanego są rozdzielone na trzy kategorie: **bezpieczne**, **natywne**i **niebezpieczne**. Słowa kluczowe mogą służyć jako nazwy klas, w których są zdefiniowane różne rodzaje punktów wejścia kodu niezarządzanego. W kodzie źródłowym te słowa kluczowe powinny być dodawane do nazwy klasy, jak w `Safe.GetTimeOfDay`, `Native.Xyz`lub `Unsafe.DangerousAPI`, na przykład. Każdy z tych słów kluczowych zapewnia przydatne informacje o zabezpieczeniach dla deweloperów korzystających z tej klasy, zgodnie z opisem w poniższej tabeli.  
  
|Słowo kluczowe|Zagadnienia dotyczące bezpieczeństwa|  
|-------------|-----------------------------|  
|**sejf**|Całkowicie nieszkodliwe dla dowolnego kodu, nawet złośliwego kodu, aby wywołać. Może być używany podobnie jak inny kod zarządzany. Na przykład funkcja, która pobiera godzinę dnia, jest zazwyczaj bezpieczna.|  
|**trybu**|Zabezpieczenia neutralne; to jest kod niezarządzany, który wymaga uprawnień do kodu niezarządzanego do wywołania. Jest zaznaczone pole wyboru zabezpieczenia, które powoduje zatrzymanie nieautoryzowanego elementu wywołującego.|  
|**unsafe**|Potencjalnie niebezpieczny punkt wejścia niezarządzanego kodu z pominięciem zabezpieczeń. Deweloperzy powinni przy użyciu takiego kodu niezarządzanego korzystać z tego, aby upewnić się, że istnieją inne zabezpieczenia, aby zapobiec luki w zabezpieczeniach. Deweloperzy muszą być odpowiedzialni, ponieważ to słowo kluczowe zastępuje system zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące bezpiecznego programowania](../../standard/security/secure-coding-guidelines.md)
