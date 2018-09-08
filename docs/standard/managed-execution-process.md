---
title: Proces zarządzanego wykonania
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- source code language
- code, managed execution process
- runtime, managed execution process
- compiling source code, managed execution process
- managed execution process
- common language runtime, managed execution process
ms.assetid: 476b03dc-2b12-49a7-b067-41caeaa2f533
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33c498e8379d68287bfe4a2e781d6797fd6b4c10
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192596"
---
# <a name="managed-execution-process"></a>Proces zarządzanego wykonania
<a name="introduction"></a> Proces zarządzanego wykonania obejmuje następujące kroki, które opisano szczegółowo w dalszej części tego tematu:  
  
1.  [Wybieranie kompilatora](#choosing_a_compiler).  
  
     Aby uzyskać korzyści dostarczane przez środowisko uruchomieniowe języka wspólnego, należy użyć co najmniej jeden Kompilatory języka przeznaczone dla środowiska uruchomieniowego.  
  
2.  [Kompilowanie kodu MSIL](#compiling_to_msil).  
  
     Kompilowanie dokonuje translacji kodu źródłowego do języka Microsoft intermediate language (MSIL) i generuje wymaganych metadanych.  
  
3.  [Kompilowanie MSIL do kodu macierzystego](#compiling_msil_to_native_code).  
  
     W czasie wykonywania kompilator just-in-time (JIT) tłumaczy MSIL w kodzie natywnym. Podczas tej kompilacji kod musi przejść proces weryfikacji, który analizuje MSIL i metadanych, aby dowiedzieć się, czy kod może być uznane za bezpieczne dla typów.  
  
4.  [Uruchamianie kodu](#running_code).  
  
     Środowisko uruchomieniowe języka wspólnego udostępnia infrastrukturę, która umożliwia wykonywanie i usług, które mogą być używane podczas wykonywania.  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>Wybieranie kompilatora  
 Aby uzyskać korzyści dostarczane przez środowisko uruchomieniowe języka wspólnego (CLR), należy użyć co najmniej jeden Kompilatory języka obiektu docelowego środowiska uruchomieniowego, takie jak Visual Basic, C#, Visual C++, F # lub jeden z wielu innych kompilatorów takie jak kompilator Eiffel, Perl lub COBOL.  
  
 Ponieważ środowisko wykonywania wielu języków, środowisko uruchomieniowe obsługuje wiele typów danych i funkcji języka. Kompilator języka, którego używasz, określa funkcji środowiska uruchomieniowego, które są dostępne i projektowania kodu przy użyciu tych funkcji. Kompilator nie środowiska uruchomieniowego, ustanawia składnię, z której należy użyć kodu. Jeśli składnik musi być całkowicie może być używany przez składników napisanych w innych językach, typów eksportowanych danego składnika musi ujawniać tylko funkcje języka, które są objęte [niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Możesz użyć <xref:System.CLSCompliantAttribute> atrybutu, aby upewnić się, że Twój kod jest zgodny ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>Kompilowanie na język MSIL  
 Podczas kompilowania do kodu zarządzanego, kompilator tłumaczy kod źródłowy do języka Microsoft intermediate language (MSIL), który jest niezależny od procesora CPU zbiór instrukcji, które mogą być skutecznie konwertowane do kodu macierzystego. MSIL zawiera instrukcje dotyczące ładowania, przechowywanie, inicjowanie i wywoływania metod obiektów, a także instrukcje dla operacji arytmetycznych i logicznych, przepływu sterowania, bezpośredni dostęp do pamięci, obsługa wyjątków i innych operacji. Przed uruchomieniem kodu MSIL muszą zostać skonwertowane do kodu specyficznego dla procesora CPU, zwykle przez [kompilator just-in-time (JIT)](#compiling_msil_to_native_code). Ponieważ środowisko uruchomieniowe języka wspólnego dostarcza co najmniej jeden kompilatory JIT dla każdej architektury komputera, który ją obsługuje, ten sam zestaw MSIL, może być kompilowany dokładnie na czas i działają w dowolnej obsługiwanej architektury.  
  
 Gdy kompilator generuje MSIL, również tworzy metadane. Metadane opisują typów w kodzie, łącznie z definicji każdego typu i podpisy członków poszczególnych typów, elementów członkowskich, które odwołuje się do kodu i innych danych, który używa środowiska uruchomieniowego, w czasie wykonywania. MSIL i metadane są zawarte w przenośny plik wykonywalny (PE) jest oparty na i rozszerzający opublikowanych Microsoft PE i wspólny format plików obiektu (COFF) używane w przeszłości, dla zawartości wykonywalnej. Tego formatu pliku, który obsługuje MSIL lub kodu natywnego, a także metadanych, umożliwia rozpoznawanie obrazów wspólnych środowiska uruchomieniowego języka systemu operacyjnego. Obecność metadane w pliku wraz z MSIL umożliwia kodzie w celu opisania siebie, co oznacza, że nie ma potrzeby bibliotek typów lub języka definicji interfejsu (IDL). Środowisko uruchomieniowe lokalizuje i wyodrębnia metadane z pliku, zgodnie z potrzebami w czasie wykonywania.  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>Kompilowanie MSIL do kodu natywnego  
 Przed uruchomieniem języka Microsoft intermediate language (MSIL), muszą być skompilowane dla środowiska uruchomieniowego języka wspólnego do kodu natywnego dla architektura komputera docelowego. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Udostępnia wykonaj tę konwersję na dwa sposoby:  
  
-   Kompilator just-in-time (JIT) .NET Framework.  
  
-   .NET Framework [Ngen.exe (Generator obrazu natywnego)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Kompilacja za pomocą kompilatora JIT  
 Kompilacja JIT konwertuje MSIL do kodu macierzystego na żądanie na czas, kiedy zawartość zestawu są ładowane i wykonywane uruchomienia aplikacji. Ponieważ środowisko uruchomieniowe języka wspólnego zawiera kompilator JIT dla każdej obsługiwanej architektury Procesora, deweloperzy mogą tworzyć zestaw zestawy MSIL, które mogą być kompilowany dokładnie na czas i działają na różnych komputerach przy użyciu architektury na innym komputerze. Jednak jeśli zarządzany kod wywołuje natywnych interfejsów API specyficznych dla platformy lub biblioteki klas specyficznych dla platformy, będzie uruchomić tylko w tym systemie operacyjnym.  
  
 Kompilacja JIT bierze pod uwagę możliwość, że jakiś kod nigdy nie może być wywoływana podczas wykonywania. Zamiast używania pamięci i czasu, aby przekonwertować wszystkie MSIL pliku PE do kodu macierzystego, konwertuje kod w języku MSIL odpowiednio do potrzeb podczas wykonywania i przechowuje wynikowy kodu natywnego w pamięci, dzięki czemu nie jest dostępny dla kolejnych wywołań w ramach tego procesu. Moduł ładujący tworzy i dołącza odcinek do każdej metody w typie, gdy typ jest ładowany i zainicjowany. Gdy metoda jest wywoływana po raz pierwszy, wycinka przekazuje sterowanie do kompilatora JIT, która konwertuje język MSIL dla tej metody w kodzie natywnym i modyfikuje wycinka bezpośrednio wskaż wygenerowanego kodu natywnego. W związku z tym kolejne wywołania do metody kompilowanego dokładnie na czas bezpośrednie przejście do kodu natywnego.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>Generowanie kodu w czasie instalacji za pomocą NGen.exe  
 Ponieważ kompilator JIT konwertuje MSIL zestawu do kodu macierzystego, podczas gdy poszczególne są wywoływane metody zdefiniowane w tym zestawie, ma to wpływ na wydajność niekorzystnie w czasie wykonywania. W większości przypadków to dopuszczalne obniżone wydajności. Co ważniejsze kod wygenerowany przez kompilator JIT jest powiązany do procesu, który wyzwolił kompilacji. Nie może być współużytkowana przez wiele procesów. Aby zezwolić na wygenerowany kod w celu udostępnienia w wielu wywołań aplikacji lub w wielu wiele procesów, które współużytkują zbiór zestawów, środowisko uruchomieniowe języka wspólnego obsługuje kompilację ahead of time. W tym trybie kompilację ahead of time używa [Ngen.exe (Generator obrazu natywnego)](../../docs/framework/tools/ngen-exe-native-image-generator.md) przekonwertować MSIL zestawy do natywnego kodu znacznie takie jak kompilator JIT wykonuje. Jednak działanie programu Ngen.exe różni się od kompilator JIT na trzy sposoby:  
  
-   Wykonuje konwersję w języku MSIL do kodu macierzystego, przed uruchomieniem aplikacji zamiast, gdy aplikacja jest uruchomiona.  
  
-   Kompiluje, aby cały zespół w czasie, zamiast jednej metody w danym momencie.  
  
-   Kod wygenerowany w pamięci podręcznej obrazów natywnych utrzymuje jako plik na dysku.  
  
### <a name="code-verification"></a>Kod weryfikacyjny  
 Jako część swojej kompilacji do kodu macierzystego kod MSIL musi pomyślnie przejść proces weryfikacji, chyba że administrator ustanowił zasady zabezpieczeń, które umożliwia kodu pomijania weryfikacji. Weryfikacji sprawdza, czy MSIL i metadanych, aby dowiedzieć się, czy kod jest bezpieczne dla typów, co oznacza, że uzyskuje dostęp do lokalizacji pamięci, który jest upoważniony do dostępu. Bezpieczeństwo typów pomaga wyizolować obiekty od siebie oraz chronić je przed przypadkowym lub złośliwym uszkodzenia. Zapewnia również zapewnienie, że ograniczeń zabezpieczeń dotyczących kodu można wymusić niezawodnie.  
  
 Środowisko uruchomieniowe opiera się na fakt, że następujące instrukcje są spełnione dla kodu, który jest weryfikowalny pod kątem bezpieczeństwa typów:  
  
-   Odwołanie do typu, jest ściśle zgodna z typem, do którego nastąpiło odwołanie.  
  
-   Jedyne operacje odpowiednio zdefiniowane są wywoływane na obiekcie.  
  
-   Tożsamości są na tym, co się podaje.  
  
 W procesie weryfikacji kodu MSIL jest badany w celu podjęcia próby potwierdzić, że kod może dostęp do lokalizacji pamięci i wywoływać metody tylko przy użyciu właściwie zdefiniowanych typów. Na przykład kod nie może dopuścić do pola obiektu były dostępne w taki sposób, który umożliwia lokalizacji pamięci można przepełnienie. Ponadto weryfikacji sprawdza kod w celu ustalenia, czy kod w języku MSIL został poprawnie wygenerowany, ponieważ niepoprawne MSIL może prowadzić do naruszenia zasad bezpieczeństwa typu. Proces weryfikacji przekazuje wyraźnie określonych kod bezpiecznego typu i przekazuje kod jest bezpiecznym typem. Jednak niektóre kod bezpiecznego typu nie może zostać przekazany weryfikacji z powodu ograniczenia procesu weryfikacji i niektórych języków zgodnie z projektem nie tworzą sprawdzalnie bezpieczny kod. Jeśli kod bezpiecznego typu jest wymagany przez zasady zabezpieczeń, ale kod nie zostały spełnione weryfikacji, wyjątek jest generowany, gdy kod jest uruchamiany.  
  
 [Powrót do początku](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>Uruchamianie kodu  
 Środowisko uruchomieniowe języka wspólnego udostępnia infrastrukturę, która umożliwia wykonanie zarządzanej została wykonana i usługi, których może być używana podczas wykonywania. Przed uruchomieniem metody muszą być skompilowane do kodu specyficznego dla procesora. Każdej metody, dla którego wygenerowano MSIL jest kompilowany dokładnie na czas, po jego jest wywoływana po raz pierwszy, a następnie uruchom. Przy następnym uruchomieniu metoda uruchomić istniejący kod natywny kompilowanego dokładnie na czas. Proces kompilacji JIT, a następnie uruchamiając kod jest powtarzany do momentu wykonania.  
  
 W czasie wykonywania kodu zarządzanego odbiera usługi, takie jak wyrzucanie elementów bezużytecznych, zabezpieczenia, współdziałanie z kodem niezarządzanym, obsługę debugowania dla wielu języków i wdrożenia rozszerzonego oraz obsługą wersjonowania.  
  
 W programie Microsoft [!INCLUDE[winxp](../../includes/winxp-md.md)] i [!INCLUDE[windowsver](../../includes/windowsver-md.md)], moduł ładujący systemu operacyjnego sprawdza, czy modułów zarządzanych, sprawdzając nieco nagłówka COFF. Bit ustawiania wskazuje, że moduł zarządzany. Jeśli moduł ładujący wykryje modułów zarządzanych, ładuje mscoree.dll, i `_CorValidateImage` i `_CorImageUnloading` powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są ładowane i zwolnione. `_CorValidateImage` wykonuje następujące czynności:  
  
1.  Zapewnia, że kod jest prawidłowy kod zarządzany.  
  
2.  Zmiany punktu wejścia w obrazie punktu wejścia w środowisku uruchomieniowym.  
  
 Na Windows 64-bitowych `_CorValidateImage` modyfikuje obrazu, który znajduje się w pamięci przez przekształcenie go z PE32 je typu PE32 + format.  
  
 [Powrót do początku](#introduction)  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie](../../docs/framework/get-started/overview.md)  
- [Niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md)  
- [Składniki samoopisujące się i metadane](../../docs/standard/metadata-and-self-describing-components.md)  
- [Ilasm.exe (asembler IL)](../../docs/framework/tools/ilasm-exe-il-assembler.md)  
- [Zabezpieczenia](../../docs/standard/security/index.md)  
- [Współdziałanie z kodem niezarządzanym](../../docs/framework/interop/index.md)  
- [Wdrażanie](../../docs/framework/deployment/net-framework-applications.md)  
- [Zestawy w środowisku uruchomieniowym CLR](../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
- [Domeny aplikacji](../../docs/framework/app-domains/application-domains.md)
