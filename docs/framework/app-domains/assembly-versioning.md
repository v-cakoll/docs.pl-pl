---
title: Przechowywanie wersji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53b757417f1f37c1a76021a518570da85dc04ad2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187325"
---
# <a name="assembly-versioning"></a>Przechowywanie wersji zestawu
Zarządzanie wszystkimi wersjami zestawów używających środowiska uruchomieniowego języka wspólnego odbywa się na poziomie zestawów. Konkretna wersja zestawu oraz wersje zestawów zależnych są rejestrowane w manifeście zestawu. Domyślna zasada dotycząca wersji środowiska dla środowiska uruchomieniowego stanowi, że aplikacje są uruchamiane tylko w wersjach, w których zostały skompilowane i przetestowane, chyba że inaczej stanowią jawnie zasady dotyczące wersji określone w plikach konfiguracji (plik konfiguracji aplikacji, plik zasad wydawcy i plik konfiguracji administratora komputera).  
  
> [!NOTE]
>  Zarządzanie wersjami dotyczy wyłącznie zestawów o silnych nazwach.  
  
 W celu rozpoznania żądania powiązania zestawu środowisko uruchomieniowe wykonuje kilka czynności:  
  
1.  Sprawdza oryginalne odwołanie do zestawu w celu ustalenia wersji zestawu, którą należy powiązać.  
  
2.  Szuka wszystkich właściwych plików konfiguracji, do których trzeba zastosować zasady dotyczące wersji.  
  
3.  Na podstawie oryginalnego odwołania do zestawu ustala poprawny zestaw oraz wszelkie przekierowania określone w plikach konfiguracji, po czym ustala wersję, która ma zostać powiązana z wywołującym zestawem.  
  
4.  Sprawdza, czy globalnej pamięci podręcznej zestawów, bazy kodów określone w plikach konfiguracji, a następnie katalog i podkatalogi, przy użyciu zasad sondowania wyjaśnionych aplikacji wyjaśnione w [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
 Poniższa ilustracja przedstawia te kroki.  
  
 ![Deklaracja extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")  
Rozpoznawanie żądania powiązania zestawu  
  
 Aby uzyskać więcej informacji na temat konfigurowania aplikacji, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md). Aby uzyskać więcej informacji na temat zasad tworzenia powiązań, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
## <a name="version-information"></a>Informacje o wersji  
 Każdy zestaw może przedstawiać informacje o wersji na dwa odrębne sposoby:  
  
-   Numer wersji zestawu, który razem z nazwą zestawu i informacjami o kulturze jest częścią tożsamości zestawu. Numer jest wykorzystywany przez środowisko uruchomieniowe do wymuszania zasad dotyczących wersji oraz odgrywa kluczową rolę w procesie rozpoznawania typów w czasie wykonywania.  
  
-   Dane informacyjne wersji, czyli ciąg tekstowy reprezentujący dodatkowe informacje o wersji dołączane są wyłącznie w celach informacyjnych.  
  
### <a name="assembly-version-number"></a>Numer wersji zestawu  
 Elementem tożsamości każdego zestawu jest jego numer wersji. W związku z tym dwa zestawy, które różnią się numerem wersji, są przez środowisko uruchomieniowe uznawane za całkowicie różne zestawy. Numer wersji jest fizycznie reprezentowany jako czteroczęściowy ciąg tekstowy o następującym formacie:  
  
 \<*Wersja główna*>.\< *wersja pomocnicza*>.\< *numer kompilacji*>.\< *poprawki*>  
  
 Na przykład wersja 1.5.1254.0 określa „1” jako wersję główną, „5” jako wersję pomocniczą, „1254” jako numer kompilacji i „0” jako numer poprawki.  
  
 Numer wersji jest przechowywany w manifeście zestawu razem z innymi informacjami tożsamości, takimi jak nazwa zestawu i klucz publiczny, a także informacjami dotyczącymi relacji i tożsamości innych zestawów połączonych z aplikacją.  
  
 Podczas kompilowania zestawu narzędzie programistyczne zapisuje informacje o zależnościach każdego zestawu, do którego istnieje odwołanie w manifeście zestawu. Na podstawie numerów wersji oraz innych informacji konfiguracyjnych wprowadzonych przez administratora, aplikację lub wydawcę środowisko uruchomieniowe ładuje odpowiednią wersję przywoływanego zestawu.  
  
 Na potrzeby zarządzania wersjami środowisko uruchomieniowe rozróżnia między zestawami zwykłymi i o silnej nazwie. Sprawdzanie wersji dotyczy tylko zestawów o silnej nazwie.  
  
 Aby uzyskać informacje dotyczące określania zasad powiązań wersji, zobacz [konfigurowania aplikacji](../../../docs/framework/configure-apps/index.md). Aby uzyskać informacje o tym, jak środowisko wykonawcze używa informacji o wersji można znaleźć określonego zestawu, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).  
  
### <a name="assembly-informational-version"></a>Informacje o wersji zestawu  
 Informacje o wersji zestawu to ciąg tekstowy, który dołącza do zestawu dodatkowe informacje o wersji jedynie w celach informacyjnych. Informacje te nie są używane w czasie wykonywania. Tekstowe informacje o wersji nawiązują do materiałów marketingowych, opakowania lub nazwy produktu. Informacjami o wersji mogą być na przykład ciągi „Środowisko uruchomieniowe języka wspólnego w wersji 1.0” lub „NET Control z dodatkiem SP 2”. W systemie Microsoft Windows w oknie dialogowym właściwości pliku na karcie Wersja informacje te są wyświetlane w polu „Wersja produktu”.  
  
> [!NOTE]
>  Można podać dowolny tekst, ale jeśli ciąg tekstowy nie będzie w formacie używanym przez numer wersji zestawu albo jeśli będzie w tym formacie, ale będzie zawierać symbole wieloznaczne, podczas kompilacji pojawi się komunikat ostrzegawczy. Ostrzeżenie to jest nieszkodliwe.  
  
 Informacje o wersji są reprezentowane za pomocą niestandardowego atrybutu <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>. Aby uzyskać więcej informacji na temat atrybutu wersji, zobacz [Konfigurowanie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md).  
  
## <a name="see-also"></a>Zobacz też  
- [Sposoby lokalizowania zestawów przez środowisko uruchomieniowe](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
- [Konfigurowanie aplikacji](../../../docs/framework/configure-apps/index.md)  
- [Ustawienie atrybutów zestawu](../../../docs/framework/app-domains/set-assembly-attributes.md)  
- [Zestawy w środowisku uruchomieniowym CLR](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
