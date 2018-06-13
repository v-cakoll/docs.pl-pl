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
ms.openlocfilehash: 4901a81e318efe8371dc72cd9c1d511d55b0c65b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578979"
---
# <a name="managed-execution-process"></a>Proces zarządzanego wykonania
<a name="introduction"></a> Proces zarządzanego wykonania obejmuje następujące kroki, które opisano szczegółowo w dalszej części tego tematu:  
  
1.  [Wybieranie kompilatora](#choosing_a_compiler).  
  
     Aby uzyskać korzyści zapewniane przez środowisko uruchomieniowe języka wspólnego, należy użyć Kompilatory języka, które odnoszą się do środowiska wykonawczego.  
  
2.  [Kompilowanie kodu do MSIL](#compiling_to_msil).  
  
     Kompilowanie kodu źródłowego przekłada się na język pośredni firmy Microsoft (MSIL) i generuje wymaganych metadanych.  
  
3.  [Kompilowanie MSIL do kodu natywnego](#compiling_msil_to_native_code).  
  
     W czasie wykonywania kompilatora just in time (JIT) tłumaczy MSIL do kodu natywnego. Podczas tej kompilacji kodu musi przejść pomyślnie proces weryfikacji, który sprawdza MSIL i metadanych, aby dowiedzieć się, czy kod można ustalić na typ bezpieczne.  
  
4.  [Wykonywanie kodu](#running_code).  
  
     Środowisko uruchomieniowe języka wspólnego udostępnia infrastrukturę, która umożliwia wykonanie miejscu i usług, które mogą być używane podczas wykonywania.  
  
<a name="choosing_a_compiler"></a>   
## <a name="choosing-a-compiler"></a>Wybieranie kompilatora  
 Aby uzyskiwać korzyści zapewniane przez środowisko uruchomieniowe języka wspólnego (CLR), należy użyć co najmniej jeden Kompilatory języka środowiska uruchomieniowego, takich jak Visual Basic, C#, Visual C++, F # lub jeden wiele kompilatorów innych firm, takich jak Eiffel, Perl lub COBOL kompilatora obiektu docelowego.  
  
 Środowiska wykonania wielu języków, dlatego środowiska uruchomieniowego obsługuje wiele typów danych oraz funkcje języka. Kompilator języka używanego określa funkcji środowiska uruchomieniowego, które są dostępne, a projektowania kod za pomocą tych funkcji. Kompilujący nie środowiska uruchomieniowego, ustanawia swój kod, należy użyć składni. Jeśli składnik musi być całkowicie używana przez składników napisanych w innych językach, typów wyeksportowanych z składników musi ujawniać tylko funkcje językowe, które znajdują się w [niezależność od języka i elementy niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md) (ZE SPECYFIKACJĄ CLS). Można użyć <xref:System.CLSCompliantAttribute> atrybutu, aby upewnić się, że kod jest zgodne ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i elementy niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_to_msil"></a>   
## <a name="compiling-to-msil"></a>Kompilowanie na MSIL  
 Podczas kompilowania do kodu zarządzanego, kompilator tłumaczy kodu źródłowego na język pośredni firmy Microsoft (MSIL), który jest niezależny od Procesora zestaw instrukcji, które można skutecznie przekonwertować kodu natywnego. MSIL zawiera instrukcje dotyczące ładowania, przechowywanie, inicjowanie i wywoływania metod obiektów, a także instrukcje dla operacji arytmetycznych i logiczne, przepływ sterowania bezpośredni dostęp do pamięci, obsługa wyjątków i innych operacji. Przed uruchomieniem kodu MSIL muszą zostać skonwertowane do kodu specyficznych dla procesora CPU, zazwyczaj przez [kompilatora just-in-time (JIT)](#compiling_msil_to_native_code). Ponieważ środowisko uruchomieniowe języka wspólnego dostarcza co najmniej jeden kompilatory JIT dla każdej architektury komputera, który ją obsługuje, ten sam zestaw MSIL można kompilacji JIT i uruchom na dowolnej obsługiwanej architektury.  
  
 Gdy kompilatora tworzy MSIL, również tworzy metadane. Metadane opisano typy w kodzie, łącznie z definicji każdego typu i podpisy członków poszczególnych typów, elementów członkowskich, które odwołuje się do kodu i innych danych, która używa środowiska wykonawczego w czasie wykonywania. MSIL i metadanych znajdują się w pliku wykonywalnego (PE) pliku przenośnego jest oparty na i który rozszerza opublikowanych PE firmy Microsoft i wspólne obiektu format pliku (COFF) używany w przeszłości do zawartości pliku wykonywalnego. Ten format pliku i bierze pod uwagę MSIL lub kodu natywnego, a także metadanych, umożliwia system operacyjny do rozpoznawania typowych obrazów środowiska uruchomieniowego języka. Obecność metadane w pliku wraz z MSIL umożliwia kodu do opisania siebie, co oznacza, że nie istnieje potrzeba dla biblioteki typów lub języka definicji interfejsu (IDL). Środowisko uruchomieniowe lokalizuje i wyodrębnianie metadanych z pliku, w razie potrzeby podczas wykonywania.  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>   
## <a name="compiling-msil-to-native-code"></a>Kompilowanie MSIL do kodu natywnego  
 Przed uruchomieniem programu Microsoft język pośredni (MSIL), muszą być skompilowane przed środowisko uruchomieniowe języka wspólnego do kodu natywnego z architekturą komputera docelowego. [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Zapewnia wykonaj tę konwersję na dwa sposoby:  
  
-   .NET Framework kompilatora just-in-time (JIT).  
  
-   .NET Framework [Ngen.exe (Generator obrazu natywnego)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Kompilacja za pomocą kompilatora JIT  
 Kompilacja JIT konwertuje MSIL do kodu natywnego na żądanie w aplikacji wykonawczego, gdy zawartość zestawu są załadowane i są stosowane. Ponieważ środowisko uruchomieniowe języka wspólnego dostarcza kompilatora JIT dla każdej obsługiwanej architektury Procesora, deweloperzy mogą tworzyć zestaw zestawy MSIL, które mogą być uruchamiane na różnych komputerach o architekturze innej maszyny i kompilacji JIT. Jednak jeśli zarządzany kod wywołuje macierzystych interfejsów API specyficzne dla platformy lub biblioteki klas specyficzne dla platformy, zostanie uruchomiony tylko w tym systemie operacyjnym.  
  
 Kompilacja JIT bierze pod uwagę możliwość kodu nigdy nie może być wywoływana podczas wykonywania. Zamiast używać pamięci i czasu, aby przekonwertować wszystkie MSIL w pliku PE kodu natywnego, konwertuje MSIL podczas wykonywania i przechowuje wynikowy kod macierzysty w pamięci, dzięki czemu nie jest dostępny dla kolejnych połączeń w ramach tego procesu. Moduł ładujący tworzy i dołącza szkielet do każdej metody w typie, gdy typ jest załadowany i zainicjowany. Gdy metoda jest wywoływana po raz pierwszy, szkielet przejmuje kontrolę przy użyciu kompilatora JIT, który konwertuje MSIL dla tej metody do kodu macierzystego i modyfikuje stub bezpośrednio wskaż wygenerowanego kodu natywnego. W związku z tym kolejne wywołania metody kompilacji JIT przejść bezpośrednio do kodu natywnego.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>Generowanie kodu w czasie instalacji za pomocą NGen.exe  
 Kompilator JIT konwertuje zestawu MSIL do kodu natywnego, podczas gdy poszczególne metody zdefiniowane w tym zestawie są nazywane, ma wpływ na wydajność niekorzystnie w czasie wykonywania. W większości przypadków, czy dopuszczalny jest obniżone wydajności. Co więcej kod wygenerowany przez kompilator JIT jest powiązany z procesu, który wywołał kompilacji. Nie może być współużytkowana przez wiele procesów. Aby zezwolić na wygenerowany kod w celu udostępnienia między wywołaniami wielu aplikacji lub wielu procesom, które współużytkują zbiór zestawów, środowisko uruchomieniowe języka wspólnego obsługuje tryb kompilacji z wyprzedzeniem o czasie. Korzysta z tego trybu kompilacji z wyprzedzeniem o czasie [Ngen.exe (Generator obrazu natywnego)](../../docs/framework/tools/ngen-exe-native-image-generator.md) przekonwertować MSIL zestawy native code znacznie jak przy użyciu kompilatora JIT jest. Jednak operacja Ngen.exe różni się od kompilatora JIT na trzy sposoby:  
  
-   Wykonuje konwersję od MSIL do kodu natywnego przed uruchomieniem aplikacji zamiast, gdy aplikacja jest uruchomiona.  
  
-   Kompiluje całego zestawu w czasie, zamiast jedną metodę naraz.  
  
-   Wygenerowany kod w buforze obrazu macierzystego go utrzymuje jako plik na dysku.  
  
### <a name="code-verification"></a>Weryfikacja kodu  
 W ramach jego kompilacji kodu natywnego kod MSIL musi przejść pomyślnie proces weryfikacji, chyba że administrator przejęło zasady zabezpieczeń, które umożliwia kod, aby pominąć weryfikacji. Weryfikacji sprawdza MSIL i metadanych, aby dowiedzieć się, czy kod jest bezpieczne, typu, co oznacza, że dostęp do lokalizacji pamięci, który jest upoważniony do dostępu. Zabezpieczenie typów pomaga wyizolować obiekty od siebie oraz ochronę przed uszkodzeniem przypadkowej lub złośliwe. Umożliwia także zapewnienie, że ograniczeń zabezpieczeń dotyczących kodu może być niezawodnie wymuszone.  
  
 Środowisko uruchomieniowe opiera się na fakt, że następujące instrukcje mają wartość true dla kodu, który jest typu sprawdzalnie bezpiecznego:  
  
-   Odwołanie do typu jest ściśle zgodna z typem, do którego nastąpiło odwołanie.  
  
-   Tylko operacje odpowiednio zdefiniowanych są wywoływane na obiekt.  
  
-   Tożsamości są, co się podaje.  
  
 W trakcie weryfikacji kodu MSIL jest sprawdzany w próba potwierdzić, że kod można uzyskać dostępu do lokalizacji pamięci i wywoływać metod tylko za pośrednictwem typów prawidłowo zdefiniowane. Na przykład kodu nie może dopuścić do pola obiektu będą dostępne w sposób umożliwiający lokalizacji pamięci można przepełnienie. Ponadto weryfikacji sprawdza kod, aby określić, czy został poprawnie wygenerowany MSIL, ponieważ niepoprawne MSIL może prowadzić do naruszenia zasad bezpieczeństwa typu. Proces weryfikacji przekazuje dobrze zdefiniowany zbiór bezpieczny kod i przekazaniem tylko kod, który jest typem bezpieczne. Jednak niektóre bezpieczny kod nie może przekazać weryfikacji z powodu pewne ograniczenia procesu weryfikacji i niektórych języków zgodnie z projektem nie daje sprawdzalnie bezpieczny kod. Jeśli bezpieczny kod jest wymagany przez zasady zabezpieczeń, ale kod nie zostały spełnione weryfikacji, jest wyjątek po uruchomieniu kodu.  
  
 [Powrót do początku](#introduction)  
  
<a name="running_code"></a>   
## <a name="running-code"></a>Wykonywanie kodu  
 Środowisko uruchomieniowe języka wspólnego oferuje infrastrukturę, która umożliwia wykonanie zarządzanych odbywa się i usług, które mogą być używane podczas wykonywania. Przed uruchomieniem metody, musi być skompilowany kod specyficznych dla procesora. Każda metoda, dla którego wygenerowano MSIL jest kompilacji JIT, gdy jest wywoływana po raz pierwszy, a następnie uruchom. Przy następnym uruchomieniu metoda uruchamiania istniejącego kodu natywnej kompilacji JIT. Proces kompilacji JIT, a następnie uruchamiając kod jest powtarzany aż do ukończenia wykonywania.  
  
 W czasie wykonywania kodu zarządzanego odbiera usług, takich jak wyrzucanie elementów bezużytecznych, zabezpieczeń, współdziałanie z kodem niezarządzanym, obsługę debugowania wielu języków i wdrożenia rozszerzonego i obsługi przechowywania wersji.  
  
 W programie Microsoft [!INCLUDE[winxp](../../includes/winxp-md.md)] i [!INCLUDE[windowsver](../../includes/windowsver-md.md)], modułu ładującego systemu operacyjnego wyszukuje modułów zarządzanych, sprawdzając nieco nagłówka COFF. Bit ustawiany oznacza modułu zarządzanego. Jeśli moduł ładujący wykryje modułów zarządzanych, ładuje biblioteki mscoree.dll, i `_CorValidateImage` i `_CorImageUnloading` modułu ładującego powiadamianie obrazy moduł zarządzany są załadowany i zwolniony. `_CorValidateImage` wykonuje następujące czynności:  
  
1.  Zapewnia, że kod jest prawidłowy kod zarządzany.  
  
2.  Punkt wejścia w obrazie zmienia się na punkt wejścia w czasie wykonywania.  
  
 W 64-bitowej wersji systemu Windows `_CorValidateImage` modyfikuje obrazu, który znajduje się w pamięci przez przekształcania z plikiem PE32 plikiem PE32 + format.  
  
 [Powrót do początku](#introduction)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../../docs/framework/get-started/overview.md)  
 [Niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md)  
 [Składniki samoopisujące się i metadane](../../docs/standard/metadata-and-self-describing-components.md)  
 [Ilasm.exe (asembler IL)](../../docs/framework/tools/ilasm-exe-il-assembler.md)  
 [Zabezpieczenia](../../docs/standard/security/index.md)  
 [Współdziałanie z kodem niezarządzanym](../../docs/framework/interop/index.md)  
 [Wdrażanie](../../docs/framework/deployment/net-framework-applications.md)  
 [Zestawy w środowisku uruchomieniowym CLR](../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [Domeny aplikacji](../../docs/framework/app-domains/application-domains.md)
