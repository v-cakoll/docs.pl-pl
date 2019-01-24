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
ms.openlocfilehash: cf9071f8b5c4569ace53b13f7b9b7282bf8e87c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711976"
---
# <a name="secure-coding-guidelines-for-unmanaged-code"></a>Wytyczne dotyczące bezpiecznego programowania dla niezarządzanego kodu
Kod biblioteki musi wywoływać kod niezarządzany (na przykład kodu natywnego interfejsów API, taką jak system Win32). Ponieważ oznacza to, że zewnętrzne obwodu zabezpieczeń dla kodu zarządzanego, właściwym Uwaga jest wymagana. Jeśli swój kod neutralnym poziomie bezpieczeństwa, zarówno kod, jak i wszelki kod, który ją wywołuje musi mieć niezarządzanych uprawnień kodu (<xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określono flagę).  
  
 Jednak często jest nieuzasadnione dla Twojego obiekt wywołujący musi mieć takie uprawnienia zaawansowane. W takich przypadkach zaufany kod może być łącząca, podobnie jak zarządzanych otoka lub kod biblioteki opisanych w [Zabezpieczanie kodu otoki](../../../docs/framework/misc/securing-wrapper-code.md). Jeśli podstawową funkcjonalność kodu niezarządzanego jest całkowicie bezpieczne, można bezpośrednio uwidaczniać; w przeciwnym razie sprawdź odpowiednie uprawnienia (żądanie) jest wymagana najpierw.  
  
 Gdy kod wywołuje kod niezarządzany, ale nie chcesz wymagać wywołujących usługi ma uprawnienia dostępu kodu niezarządzanego, musi assert prawo. Potwierdzenie blokuje przejście przez stos w swojej ramki. Należy uważać, aby nie utworzyć lukę w zabezpieczeniach w ramach tego procesu. Zwykle oznacza to, musi popytu odpowiednie uprawnienie swoje obiekty wywołujące i następnie wykonywać tylko pozwala to uprawnienie i nie więcej za pomocą kodu niezarządzanego. W niektórych przypadkach (na przykład, pory dnia funkcji get) niezarządzanego kodu mogą bezpośrednio łączyć się z wywołującym bez żadnych kontroli zabezpieczeń. W każdym przypadku wszelki kod, który potwierdza musi ponosi odpowiedzialność za zabezpieczenia.  
  
 Ponieważ dowolnego kodu zarządzanego, który zawiera ścieżkę kodu do kodu macierzystego potencjalnych celów dla złośliwego kodu, określania niezarządzanego kodu można go bezpiecznie używać i jak należy użyć wymaga rozwagą. Ogólnie rzecz biorąc kodem niezarządzanym powinno nigdy bezpośrednio uwidaczniać częściowo zaufanych wywołań. Istnieją dwa podstawowych zagadnień podczas oceny bezpieczeństwa użytkowania kodu niezarządzanego w bibliotekach, które są wywoływane przez częściowo zaufany kod:  
  
-   **Funkcje**. Niezarządzany interfejs API zapewnia funkcje, które nie zezwala na obiekty wywołujące do wykonywania operacji potencjalnie niebezpiecznych? Zabezpieczenia dostępu kodu używa uprawnień do wymuszenia dostępu do zasobów, dlatego należy rozważyć czy interfejs API korzysta z plików, interfejs użytkownika lub wątkowości, lub czy uwidacznia on informacje chronione. Jeśli tak jest, kod zarządzany, zawijanie go musi popytu niezbędne uprawnienia przed zezwoleniem na jego ma zostać nawiązane. Ponadto gdy nie są chronione przez uprawnienia, dostęp do pamięci musi być ograniczone do ścisłe zasady bezpieczeństwa.  
  
-   **Sprawdzanie parametrów**. Typowe przebiegów ataku nieoczekiwany parametry, aby widoczne metod kodu niezarządzanego interfejsu API w celu podjęcia próby spowoduje ich działają poza specyfikacji. Przy użyciu indeksu spoza zakresu przekroczenia buforu lub wartości przesunięcia są jednym z typowych przykładów ten rodzaj ataku, są wszystkie parametry, które mogą wykorzystać usterki w kodzie podstawowym. W związku z tym nawet jeśli kodu niezarządzanego interfejsu API jest funkcjonalnie bezpieczne (po niezbędne wymagania) dla częściowo zaufanego obiektów wywołujących, zarządzane kodu musi również wyboru parametr ważności wyczerpująco, aby upewnić się, że nie wywołuje niepożądanych możliwe od złośliwego kodu za pomocą zarządzanych Kod otoki warstwy.  
  
## <a name="using-suppressunmanagedcodesecurityattribute"></a>Korzystanie z SuppressUnmanagedCodeSecurityAttribute  
 Jest aspektem wydajności potwierdzające i następnie wywoływania niezarządzanego kodu. Za każde wywołanie systemu zabezpieczeń automatycznie zażąda uprawnień kodu niezarządzanego, wynikiem przeszukiwania stosu każdorazowo. Jeśli potwierdzenia i natychmiast wywoływać kod niezarządzany, przejście przez stos może być całkowicie nieprzydatna: składa się z Twojego assert i wywołania kodu niezarządzanego.  
  
 Niestandardowy atrybut o nazwie <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> mogą być stosowane do kodu niezarządzanego punktami wejściowymi umożliwiającymi Wyłącz sprawdzanie zabezpieczeń normalne, która żąda <xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określone uprawnienie. Należy zachować wyjątkową ostrożność zawsze muszą zostać podjęte, gdy to zrobić, ponieważ ta akcja powoduje utworzenie Otwieranie drzwi do kodu niezarządzanego z żadnych zabezpieczeń środowisko uruchomieniowe sprawdza. Należy zauważyć, że nawet w przypadku **SuppressUnmanagedCodeSecurityAttribute** stosowany, jest sprawdzanie jednorazowe zabezpieczeń, które odbywa się na kompilacji just-in-time (JIT), aby upewnić się, że bezpośredniego obiektu wywołującego ma uprawnienia do wywołania kod niezarządzany.  
  
 Jeśli używasz **SuppressUnmanagedCodeSecurityAttribute**, sprawdź następujące kwestie:  
  
-   Wprowadź punkt wejścia do kodu niezarządzanego wewnętrznych lub w inny sposób niedostępny poza kodem.  
  
-   Każde wywołanie do kodu niezarządzanego jest potencjalnym lukę w zabezpieczeniach. Upewnij się, że Twój kod nie jest portal dla złośliwego kodu pośrednio wywołania kodu niezarządzanego i unikanie sprawdzanie zabezpieczeń. Wymaga uprawnień, jeśli to stosowne.  
  
-   Użyj konwencji nazewnictwa, aby jawnie identyfikować podczas tworzenia niebezpiecznych ścieżkę do kodu niezarządzanego, zgodnie z opisem w dalszej części tego artykułu...  
  
## <a name="naming-convention-for-unmanaged-code-methods"></a>Konwencje nazewnictwa dla metod kodu niezarządzanego  
 Konwencja przydatne i zdecydowanie zalecane została ustanowiona dla nazw metod kodu niezarządzanego. Wszystkie metody niezarządzanego kodu są podzielone na trzy kategorie: **bezpieczne**, **natywnych**, i **niebezpieczne**. Tych słów kluczowych mogą służyć jako nazwy klas, w których zdefiniowano różne rodzaje punkty wejścia kodu niezarządzanego. W kodzie źródłowym, te słowa kluczowe należy dodać do nazwy klasy, podobnie jak w `Safe.GetTimeOfDay`, `Native.Xyz`, lub `Unsafe.DangerousAPI`, na przykład. Każda z tych słów kluczowych zawiera informacje o zabezpieczeniach przydatny dla deweloperów korzystających z tej klasy, zgodnie z opisem w poniższej tabeli.  
  
|Słowo kluczowe|Zagadnienia dotyczące bezpieczeństwa|  
|-------------|-----------------------------|  
|**Bezpieczne**|Nieszkodliwy całkowicie dowolnego kodu, nawet złośliwego kodu, aby wywołać. Może służyć podobnie jak inne kodu zarządzanego. Na przykład funkcja, która pobiera godzinę jest zazwyczaj bezpieczne.|  
|**native**|Neutralnym poziomie bezpieczeństwa; oznacza to, że kod niezarządzany, który wymaga niezarządzany kod uprawnienia do wywołania. Zabezpieczenia są sprawdzane, co uniemożliwia nieautoryzowanym obiektu wywołującego.|  
|**unsafe**|Niebezpieczny kod niezarządzany punkt wejścia z zabezpieczeniami pominięte. Deweloperzy należy zachować ostrożność największy podczas korzystania z takiego kodu niezarządzanego, upewniając się, że innych mechanizmów ochrony znajdują się w miejscu, aby uniemożliwić luki w zabezpieczeniach. Deweloperzy muszą być odpowiedzialne, to słowo kluczowe zastępuje system zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz także
- [Wytyczne dotyczące bezpiecznego programowania](../../../docs/standard/security/secure-coding-guidelines.md)
