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
ms.openlocfilehash: 3cfe66f188c5abf245370f841d4b4d31e7b6db8b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290074"
---
# <a name="managed-execution-process"></a>Proces zarządzanego wykonania
<a name="introduction"></a>Zarządzany proces wykonywania obejmuje następujące kroki, które opisano szczegółowo w dalszej części tego tematu:  
  
1. [Wybieranie kompilatora](#choosing_a_compiler).  
  
     Aby uzyskać korzyści zapewniane przez środowisko uruchomieniowe języka wspólnego, należy użyć co najmniej jednego kompilatora języka, który jest przeznaczony dla środowiska uruchomieniowego.  
  
2. [Kompilowanie kodu do MSIL](#compiling_to_msil).  
  
     Kompilowanie tłumaczy kod źródłowy do języka pośredniego firmy Microsoft (MSIL) i generuje wymagane metadane.  
  
3. [Kompilowanie MSIL do kodu natywnego](#compiling_msil_to_native_code).  
  
     W czasie wykonywania kompilator just-in-Time (JIT) tłumaczy MSIL na kod natywny. W trakcie tej kompilacji kod musi przejść proces weryfikacji, który sprawdza MSIL i metadane, aby dowiedzieć się, czy kod można ustalić jako bezpieczny.  
  
4. [Uruchamianie kodu](#running_code).  
  
     Środowisko uruchomieniowe języka wspólnego zapewnia infrastrukturę, która umożliwia wykonywanie i korzystanie z usług, których można użyć podczas wykonywania.  
  
<a name="choosing_a_compiler"></a>
## <a name="choosing-a-compiler"></a>Wybieranie kompilatora  
 Aby uzyskać korzyści zapewniane przez środowisko uruchomieniowe języka wspólnego (CLR), należy użyć co najmniej jednego kompilatora języka, który jest przeznaczony dla środowiska uruchomieniowego, takiego jak Visual Basic, C#, Visual C++, F # lub jeden z wielu kompilatorów innych firm, takich jak Eiffel, Perl lub COBOL.  
  
 Ponieważ jest to środowisko wykonywania wielu języków, środowisko uruchomieniowe obsługuje szeroką gamę typów danych i funkcji językowych. Używany kompilator języka określa, które funkcje środowiska uruchomieniowego są dostępne i projektujesz kod przy użyciu tych funkcji. Kompilator, a nie środowisko uruchomieniowe, określa składnię, której kod musi używać. Jeśli składnik musi być całkowicie użyteczny przez składniki w innych językach, wyeksportowane typy składników muszą uwidaczniać tylko funkcje języka, które są zawarte w [niezależności od języka i składnikach niezależnych od języka](language-independence-and-language-independent-components.md) (CLS). Możesz użyć atrybutu, <xref:System.CLSCompliantAttribute> Aby upewnić się, że kod jest zgodny ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md).  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_to_msil"></a>
## <a name="compiling-to-msil"></a>Kompilowanie do MSIL  
 Podczas kompilowania do kodu zarządzanego kompilator tłumaczy kod źródłowy do języka pośredniego firmy Microsoft (MSIL), który jest zestawem instrukcji zależnych od procesora CPU, które mogą być efektywnie konwertowane na kod natywny. MSIL zawiera instrukcje dotyczące ładowania, przechowywania, inicjowania i wywoływania metod dla obiektów, a także instrukcje dotyczące operacji arytmetycznych i logicznych, przepływu sterowania, bezpośredniego dostępu do pamięci, obsługi wyjątków i innych operacji. Aby można było uruchomić kod, MSIL musi być konwertowany na kod specyficzny dla procesora CPU, zazwyczaj przez [kompilator just-in-Time (JIT)](#compiling_msil_to_native_code). Ponieważ środowisko uruchomieniowe języka wspólnego dostarcza co najmniej jeden kompilator JIT dla każdej obsługiwanej architektury komputera, ten sam zestaw MSIL może być skompilowany w sposób JIT i uruchamiany w dowolnej z obsługiwanych architektur.  
  
 Gdy kompilator tworzy MSIL, generuje również metadane. Metadane opisują typy w kodzie, w tym definicję każdego typu, sygnatury elementów członkowskich każdego typu, elementy członkowskie, do których odwołuje się kod, oraz inne dane używane przez środowisko uruchomieniowe w czasie wykonywania. MSIL i metadane są zawarte w przenośnym pliku wykonywalnym (PE), który jest oparty na systemie i który rozszerza opublikowany plik Microsoft PE i format Common Object File (COFF) używany historycznie dla zawartości wykonywalnej. Ten format pliku, który uwzględnia kod MSIL lub natywny, a także metadane, umożliwia systemowi operacyjnemu rozpoznawanie obrazów środowiska uruchomieniowego języka wspólnego. Obecność metadanych w pliku wraz z MSIL pozwala na opisywanie kodu, co oznacza, że nie ma potrzeby stosowania bibliotek typów ani języka definicji interfejsu (IDL). Środowisko uruchomieniowe lokalizuje i wyodrębnia metadane z pliku zgodnie z wymaganiami podczas wykonywania.  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>
## <a name="compiling-msil-to-native-code"></a>Kompilowanie MSIL do kodu natywnego  
 Zanim będzie możliwe uruchomienie języka pośredniego firmy Microsoft (MSIL), należy go skompilować względem środowiska uruchomieniowego języka wspólnego do kodu natywnego dla architektury maszyny docelowej. .NET Framework zapewnia dwa sposoby przeprowadzenia tej konwersji:  
  
- .NET Framework kompilator just-in-Time (JIT).  
  
- .NET Framework [Ngen. exe (Generator obrazu natywnego)](../framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Kompilacja przez kompilator JIT  
 Kompilacja JIT konwertuje MSIL na kod natywny na żądanie w czasie wykonywania aplikacji, gdy zawartość zestawu jest ładowana i wykonywana. Ponieważ środowisko uruchomieniowe języka wspólnego dostarcza kompilator JIT dla każdej obsługiwanej architektury procesora, deweloperzy mogą tworzyć zestawy zestawów MSIL, które mogą być kompilowane w trybie JIT i uruchamiane na różnych komputerach z różnymi architekturami komputera. Jeśli jednak kod zarządzany wywołuje natywne interfejsy API specyficzne dla platformy lub bibliotekę klas specyficznych dla platformy, będzie działać tylko w tym systemie operacyjnym.  
  
 Kompilacja JIT bierze pod uwagę możliwość, że jakiś kod może nigdy nie być wywoływany podczas wykonywania. Zamiast używać czasu i pamięci do konwersji wszystkich MSIL w pliku PE na kod natywny, konwertuje MSIL zgodnie z wymaganiami podczas wykonywania i przechowuje kod natywny w pamięci, tak aby był dostępny do kolejnych wywołań w kontekście tego procesu. Moduł ładujący tworzy i dołącza skrót do każdej metody w typie, gdy typ jest ładowany i zainicjowany. Gdy metoda jest wywoływana po raz pierwszy, szczątkowa przekazuje kontrolę do kompilatora JIT, który konwertuje MSIL dla tej metody na kod natywny i modyfikuje punkt wejścia bezpośrednio do wygenerowanego kodu natywnego. W związku z tym kolejne wywołania metody skompilowanej JIT przechodzą bezpośrednio do kodu natywnego.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>Generowanie kodu w czasie instalacji przy użyciu programu NGen. exe  
 Ponieważ kompilator JIT konwertuje plik MSIL zestawu na kod natywny, gdy są wywoływane poszczególne metody zdefiniowane w tym zestawie, wpływ na wydajność jest niekorzystny w czasie wykonywania. W większości przypadków, że zmniejszana wydajność jest akceptowalna. Co ważniejsze, kod wygenerowany przez kompilator JIT jest powiązany z procesem, który wyzwolił kompilację. Nie może być współużytkowana przez wiele procesów. Aby zezwolić na udostępnianie wygenerowanego kodu między wieloma wywołaniami aplikacji lub wieloma procesami, które współużytkują zestaw zestawów, środowisko uruchomieniowe języka wspólnego obsługuje tryb kompilacji z wyprzedzeniem. Ten tryb kompilacji przed czasem używa programu [Ngen. exe (Generator obrazu natywnego)](../framework/tools/ngen-exe-native-image-generator.md) do konwertowania zestawów MSIL na kod natywny, podobnie jak kompilator JIT. Jednak operacja programu Ngen. exe różni się od kompilatora JIT na trzy sposoby:  
  
- Wykonuje konwersję z języka MSIL do kodu natywnego przed uruchomieniem aplikacji, a nie w czasie, gdy aplikacja jest uruchomiona.  
  
- Kompiluje cały zestaw jednocześnie zamiast jednej metody w danym momencie.  
  
- Zachowuje wygenerowany kod w pamięci podręcznej obrazów natywnych jako plik na dysku.  
  
### <a name="code-verification"></a>Weryfikacja kodu  
 W ramach kompilacji do kodu natywnego, kod MSIL musi przejść proces weryfikacji, chyba że administrator ustanowił zasady zabezpieczeń, które pozwalają kodowi pominąć weryfikację. Weryfikacja sprawdza MSIL i metadane, aby dowiedzieć się, czy kod jest bezpieczny, co oznacza, że uzyskuje dostęp tylko do lokalizacji pamięci, do której ma dostęp. Bezpieczeństwo typów ułatwia izolowanie obiektów od siebie i pomaga chronić je przed przypadkowym lub złośliwym uszkodzeniem. Zapewnia również gwarancję, że ograniczenia zabezpieczeń w kodzie mogą być niezawodnie wymuszane.  
  
 Środowisko uruchomieniowe polega na tym, że prawdziwe są następujące instrukcje dla kodu, który jest typu "bezpieczny":  
  
- Odwołanie do typu jest ściśle zgodne z typem, do którego się odwołuje.  
  
- Tylko odpowiednio zdefiniowane operacje są wywoływane w obiekcie.  
  
- Tożsamości to te, do których są one zgłaszane.  
  
 W trakcie procesu weryfikacji kod MSIL jest sprawdzany w próbie potwierdzenia, że kod może uzyskać dostęp do lokalizacji pamięci i wywołać metody tylko za pomocą poprawnie zdefiniowanych typów. Na przykład kod nie może zezwalać na dostęp do pól obiektu w sposób, który pozwala na przepełnienie lokalizacji pamięci. Ponadto weryfikacja sprawdza kod, aby określić, czy MSIL zostało prawidłowo wygenerowane, ponieważ nieprawidłowe MSIL może prowadzić do naruszenia reguł bezpieczeństwa typów. Proces weryfikacji przekazuje dobrze zdefiniowany zestaw bezpiecznego kodu i przekazuje tylko kod, który jest bezpiecznym typem. Niemniej jednak kod bezpieczny dla typu może nie przekazywać weryfikacji z powodu niektórych ograniczeń procesu weryfikacji, a w niektórych językach, przez zaprojektowanie, nie generują kodu z bezpiecznym typem. Jeśli zasady zabezpieczeń wymagają kodu z bezpiecznym typem, ale kod nie przeszedł weryfikacji, wyjątek jest zgłaszany podczas uruchamiania kodu.  
  
 [Powrót do początku](#introduction)  
  
<a name="running_code"></a>
## <a name="running-code"></a>Uruchamianie kodu  
 Środowisko uruchomieniowe języka wspólnego udostępnia infrastrukturę, która umożliwia zarządzanie wykonywaniem i usługami, które mogą być używane podczas wykonywania. Aby można było uruchomić metodę, należy ją skompilować do kodu specyficznego dla procesora. Każda metoda, dla której Wygenerowano MSIL, jest skompilowana w trybie JIT, gdy jest wywoływana po raz pierwszy, a następnie uruchamiana. Przy następnym uruchomieniu metody zostanie uruchomiony istniejący kod natywny skompilowany przez JIT. Proces kompilowania JIT i uruchamiania kodu jest powtarzany, dopóki wykonywanie nie zostanie ukończone.  
  
 Podczas wykonywania kod zarządzany odbiera usługi takie jak odzyskiwanie pamięci, zabezpieczenia, współdziałanie z kodem niezarządzanym, obsługa debugowania przez wiele języków oraz Ulepszona obsługa wdrażania i przechowywania wersji.  
  
 W systemie Microsoft Windows Vista moduł ładujący systemu operacyjnego sprawdza dla modułów zarządzanych, sprawdzając bit w nagłówku COFF. Bit ustawiany oznacza moduł zarządzany. Jeśli moduł ładujący wykryje moduły zarządzane, ładuje mscoree. dll i `_CorValidateImage` `_CorImageUnloading` powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są ładowane i zwalniane. `_CorValidateImage`wykonuje następujące akcje:  
  
1. Zapewnia, że kod jest prawidłowym kodem zarządzanym.  
  
2. Zmienia punkt wejścia w obrazie na punkt wejścia w środowisku uruchomieniowym.  
  
 W 64-bitowym systemie Windows program `_CorValidateImage` modyfikuje obraz znajdujący się w pamięci, przekształcając go z PE32 na PE32 + format.  
  
 [Powrót do początku](#introduction)  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie](../framework/get-started/overview.md)
- [Niezależność od języka i składniki niezależne od języka](language-independence-and-language-independent-components.md)
- [Metadane i składniki do samoopisywania](metadata-and-self-describing-components.md)
- [Ilasm. exe (Asembler IL)](../framework/tools/ilasm-exe-il-assembler.md)
- [Bezpieczeństwo](security/index.md)
- [Współdziałanie z kodem niezarządzanym](../framework/interop/index.md)
- [Wdrożenie](../framework/deployment/net-framework-applications.md)
- [Zestawy w środowisku .NET](assembly/index.md)
- [Domeny aplikacji](../framework/app-domains/application-domains.md)
