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
ms.openlocfilehash: 60e293ac8c9100876aa5a524bb5dda04e9f4183f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu
Kod biblioteki musi wywoływać kodu niezarządzanego (na przykład kodu natywnego interfejsów API, takich jak Win32). Ponieważ oznacza to, że zewnętrzne granicznej zabezpieczeń dla zarządzanego kodu właściwym ostrożność jest wymagana. Jeśli kod jest neutralnym poziomie bezpieczeństwa, zarówno w kodzie, jak i każdy kod wywołujący go musi mieć niezarządzanych uprawnień kodu (<xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określona flaga).  
  
 Często jest jednak nieuzasadnione z obiektu wywołującego takie zaawansowanych uprawnień. W takim przypadku zaufany kod może być łącząca, podobnie jak zarządzany otok lub kod biblioteki opisanych w [Zabezpieczanie kodu otoki](../../../docs/framework/misc/securing-wrapper-code.md). W przypadku całkowicie bezpieczne funkcjonalność kodu niezarządzanego, można bezpośrednio widoczne; w przeciwnym razie sprawdź odpowiednie uprawnienia (żądanie) jest wymagana najpierw.  
  
 Jeśli kod wywołuje do kodu niezarządzanego, ale nie chcesz wymagać Twojej wywołującym ma uprawnienia dostępu do kodu niezarządzanego, musi assert prawo. Potwierdzenie blokuje przeszukiwania stosu w Twojej ramki. Należy zachować ostrożność, że nie należy tworzyć luka w zabezpieczeniach w tym procesie. Zwykle oznacza to, należy zażądać odpowiednie uprawnienia z obiektów wywołujących i następnie użyć kodu niezarządzanego, aby wykonać tylko umożliwia uprawnienie i nie więcej. W niektórych przypadkach (na przykład funkcję czasu dnia get) kodu niezarządzanego może bezpośrednio widoczne dla wywołań bez kontroli zabezpieczeń. W każdym przypadku kodu, który potwierdza, należy wykonać odpowiedzialność za bezpieczeństwo.  
  
 Ponieważ zarządzanego kodu, który zawiera ścieżkę kodu do kodu macierzystego potencjalnych celu złośliwego kodu, określania, które niezarządzanego kodu może być bezpiecznie stosowany, i jak należy go używać wymaga rozwagą. Ogólnie rzecz biorąc niezarządzany kod powinien nigdy być bezpośrednio widoczne dla częściowo zaufanych wywołań. Istnieją dwa podstawowe zagadnienia dotyczące podczas obliczania bezpieczeństwa niezarządzany kod używany w bibliotekach, które zostały wywołane przez częściowo zaufany kod:  
  
-   **Funkcje**. Niezarządzanego API oferuje funkcje, które nie zezwala na obiekty wywołujące do wykonywania operacji potencjalnie niebezpiecznych? Zabezpieczenia dostępu kodu używa uprawnień do wymuszenia dostępu do zasobów, dlatego należy rozważyć czy interfejs API korzysta z plików, interfejs użytkownika lub wątkowość, lub czy ujawnia chronione informacje. Jeśli tak, kodu zarządzanego zawijania go musi żądać niezbędne uprawnienia przed dzięki któremu można wprowadzić. Ponadto gdy nie jest chroniony przez uprawnienia, dostęp do pamięci musi być ograniczone do ścisłe zasady zabezpieczeń.  
  
-   **Sprawdzanie parametru**. Typowe przekazuje ataku nieoczekiwany parametry widoczne metody kodu niezarządzanego API próby spowodować działać poza specyfikacji. Przepełnienia buforów przy użyciu indeksu out-of-range lub wartości przesunięcia są typowe przykładem takiego ataku, jak to wszystkie parametry, które może wykorzystać usterkę kodu źródłowego. W związku z tym nawet jeśli kodu niezarządzanego interfejsu API jest funkcjonalnie bezpieczne (po niezbędne wymagania) częściowo zaufany wywołań zarządzanych kodu musi również wyboru parametr ważności wyczerpujący w celu zapewnienia możliwości z złośliwego kodu za pomocą zarządzanego nie niezamierzone wywołań Kod otoki warstwy.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Korzystanie z SuppressUnmanagedCodeSecurityAttribute  
 Jest elementem wydajności zostanie i następnie wywoływanie kodu niezarządzanego. Dla każdego wywołania systemu zabezpieczeń automatycznie wymaga uprawnień kodu niezarządzanego, co przeszukiwania stosu zawsze. Jeśli Potwierdzaj i natychmiast wywoływanie kodu niezarządzanego, przeszukiwania stosu może być znaczenia: składa się z Twojego assert i wywołania kodu niezarządzanego.  
  
 Niestandardowy atrybut o nazwie <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> może odnosić się do punktów wejścia kodu niezarządzanego, aby wyłączyć sprawdzanie zabezpieczeń normalne, która żąda <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> uprawnienia określone. Zawsze należy podjąć wyjątkową ostrożność podczas sprawdza temu, ponieważ ta akcja powoduje otwieranie drzwi do kodu niezarządzanego z żadnych zabezpieczeń środowiska wykonawczego. Należy zauważyć, że nawet w przypadku **SuppressUnmanagedCodeSecurityAttribute** zastosowane, Brak wyboru jednorazowe zabezpieczeń, wykonywanej w kompilacji just-in-time (JIT), aby upewnić się, że bezpośredniego obiektu wywołującego ma uprawnienia do wywoływania niezarządzany kod.  
  
 Jeśli używasz **SuppressUnmanagedCodeSecurityAttribute**, sprawdź następujące kwestie:  
  
-   Należy punktu wejścia kodu niezarządzanego wewnętrznych lub w inny sposób niedostępny poza swój kod.  
  
-   Wszystkie wywołania do kodu niezarządzanego jest potencjalnych luka w zabezpieczeniach. Upewnij się, że kod nie jest portal dla złośliwego kodu pośrednio wywoływać kodu niezarządzanego i uniknąć sprawdzanie zabezpieczeń. Żądanie uprawnienia, w razie potrzeby.  
  
-   Użyj konwencji nazewnictwa, aby jednoznacznie zidentyfikować podczas tworzenia niebezpiecznych ścieżki do kodu niezarządzanego, zgodnie z opisem w poniższej sekcji..  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Konwencja nazewnictwa dla metod niezarządzany kod  
 Konwencja przydatne i zdecydowanie zalecane została ustanowiona dla nazwy metody kodu niezarządzanego. Wszystkie metody kodu niezarządzanego są podzielone na trzy kategorie: **bezpieczne**, **natywnego**, i **niebezpieczne**. Słowa kluczowe może służyć jako nazwy klasy, w których zdefiniowano różne rodzaje punkty wejścia kodu niezarządzanego. W kodzie źródłowym słowa kluczowe powinny zostać dodane do nazwy klasy, jak w `Safe.GetTimeOfDay`, `Native.Xyz`, lub `Unsafe.DangerousAPI`, np. Każda z następujących słów kluczowych informacje przydatne zabezpieczeń dla deweloperów korzystających z tej klasy, zgodnie z opisem w poniższej tabeli.  
  
|Słowo kluczowe|Zagadnienia dotyczące bezpieczeństwa|  
|-------------|-----------------------------|  
|**Bezpieczne**|Całkowicie nieszkodliwe dla żadnego kodu nawet złośliwy kod, aby wywołać. Można tak samo jak inne kodu zarządzanego. Na przykład funkcja, która pobiera godzinę jest zazwyczaj bezpieczne.|  
|**Natywny**|Neutralnym poziomie bezpieczeństwa; oznacza to, że kodu niezarządzanego, który wymaga niezarządzany kod uprawnienia do wywoływania. Zabezpieczenia są sprawdzane, co uniemożliwia nieautoryzowanym wywołującego.|  
|**unsafe**|Niebezpieczny kod niezarządzany punkt wejścia z zabezpieczeniami pomijane. Deweloperzy należy zachować ostrożność największy podczas korzystania z takich kodu niezarządzanego, upewniając się, że inne ochrony znajdują się w miejscu, aby uniemożliwić luki w zabezpieczeniach. Deweloperzy muszą być odpowiedzialne, jak system zabezpieczeń zastępuje to słowo kluczowe.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
