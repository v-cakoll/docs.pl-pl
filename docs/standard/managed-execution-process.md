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
ms.openlocfilehash: 46a266849f137076170287aeb10becedf83ccf78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160225"
---
# <a name="managed-execution-process"></a>Proces zarządzanego wykonania
<a name="introduction"></a>Proces wykonywania zarządzanego obejmuje następujące kroki, które zostały szczegółowo omówione w dalszej części tego tematu:  
  
1. [Wybór kompilatora](#choosing_a_compiler).  
  
     Aby uzyskać korzyści dostarczane przez program runtime języka wspólnego, należy użyć jednego lub więcej kompilatorów języka, które są przeznaczone dla czasu wykonywania.  
  
2. [Kompilowanie kodu do MSIL](#compiling_to_msil).  
  
     Kompilowanie tłumaczy kod źródłowy na język pośredni firmy Microsoft (MSIL) i generuje wymagane metadane.  
  
3. [Kompilowanie MSIL do kodu macierzystego](#compiling_msil_to_native_code).  
  
     W czasie wykonywania kompilator just-in-time (JIT) tłumaczy MSIL do kodu macierzystego. Podczas tej kompilacji kod musi przekazać proces weryfikacji, który sprawdza MSIL i metadanych, aby dowiedzieć się, czy kod można określić jako bezpieczny typ.  
  
4. [Uruchamianie kodu](#running_code).  
  
     Czas wykonywania języka wspólnego zapewnia infrastrukturę, która umożliwia wykonanie odbywa ć i usług, które mogą być używane podczas wykonywania.  
  
<a name="choosing_a_compiler"></a>
## <a name="choosing-a-compiler"></a>Wybieranie kompilatora  
 Aby uzyskać korzyści zapewniane przez program runtime języka wspólnego (CLR), należy użyć jednego lub więcej kompilatorjęzyka, które są przeznaczone dla czasu wykonywania, takich jak Visual Basic, C#, Visual C++, F#, lub jeden z wielu kompilatorów innych firm, takich jak Kompilat Eiffel, Perl lub COBOL.  
  
 Ponieważ jest to środowisko wykonywania w wielu językach, środowisko wykonawcze obsługuje szeroką gamę typów danych i funkcji języka. Kompilator języka, którego używasz określa, które funkcje wykonywania są dostępne i zaprojektować kod przy użyciu tych funkcji. Kompilator, a nie w czasie wykonywania, ustanawia składnię kod musi używać. Jeśli składnik musi być w pełni użyteczny przez składniki napisane w innych językach, eksportowane typy składnika muszą uwidaczniać tylko funkcje języka, które są zawarte w [składnikach niezależnych od języka i niezależnych od języka](../../docs/standard/language-independence-and-language-independent-components.md) (CLS). Atrybutu można <xref:System.CLSCompliantAttribute> użyć, aby upewnić się, że kod jest zgodny ze specyfikacją CLS. Aby uzyskać więcej informacji, zobacz [Niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md).  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_to_msil"></a>
## <a name="compiling-to-msil"></a>Kompilowanie do MSIL  
 Podczas kompilowania do kodu zarządzanego kompilator tłumaczy kod źródłowy na język pośredni firmy Microsoft (MSIL), który jest niezależnym od procesora zestawu instrukcji, które można skutecznie przekonwertować na kod macierzysty. MSIL zawiera instrukcje dotyczące ładowania, przechowywania, inicjowania i wywoływania metod na obiektach, a także instrukcje dotyczące operacji arytmetycznych i logicznych, przepływu sterowania, bezpośredniego dostępu do pamięci, obsługi wyjątków i innych operacji. Przed uruchomieniem kodu MSIL musi zostać przekonwertowany na kod specyficzny dla procesora CPU, zwykle przez [kompilator just-in-time (JIT).](#compiling_msil_to_native_code) Ponieważ program runtime języka wspólnego dostarcza co najmniej jeden kompilator JIT dla każdej architektury komputera, który obsługuje, ten sam zestaw MSIL może być kompilowany przez JIT i uruchamiany na dowolnej obsługiwanej architekturze.  
  
 Gdy kompilator tworzy MSIL, również tworzy metadane. Metadane opisuje typy w kodzie, w tym definicji każdego typu, podpisy członków każdego typu, członków, które odwołuje się do kodu i inne dane, które czas wykonywania używa w czasie wykonywania. MSIL i metadane są zawarte w przenośnym pliku wykonywalnym (PE), który jest oparty na i który rozszerza opublikowany microsoft PE i wspólny format pliku obiektu (COFF) używany w przeszłości dla zawartości wykonywalnej. Ten format pliku, który obsługuje MSIL lub kod macierzysty, a także metadane, umożliwia systemowi operacyjnemu rozpoznawanie typowych obrazów w czasie wykonywania języka. Obecność metadanych w pliku wraz z MSIL umożliwia kod do opisania się, co oznacza, że nie ma potrzeby bibliotek typów lub języka definicji interfejsu (IDL). Czas wykonywania lokalizuje i wyodrębnia metadane z pliku zgodnie z potrzebami podczas wykonywania.  
  
 [Powrót do początku](#introduction)  
  
<a name="compiling_msil_to_native_code"></a>
## <a name="compiling-msil-to-native-code"></a>Kompilowanie MSIL do kodu macierzystego  
 Przed uruchomieniem języka pośredniego firmy Microsoft (MSIL), musi być skompilowany względem wspólnego języka wykonywania do kodu macierzystego dla architektury komputera docelowego. Program .NET Framework udostępnia dwa sposoby wykonania tej konwersji:  
  
- Kompilator just-in-time (JIT) programu .NET Framework.  
  
- Program .NET Framework [Ngen.exe (natywny generator obrazów)](../../docs/framework/tools/ngen-exe-native-image-generator.md).  
  
### <a name="compilation-by-the-jit-compiler"></a>Kompilacja przez kompilator JIT  
 Kompilacja JIT konwertuje MSIL do kodu macierzystego na żądanie w czasie wykonywania aplikacji, gdy zawartość zestawu są ładowane i wykonywane. Ponieważ program runtime języka wspólnego dostarcza kompilator JIT dla każdej obsługiwanej architektury procesora CPU, deweloperzy mogą tworzyć zestaw zestawów MSIL, które mogą być kompilowane jit i uruchamiane na różnych komputerach z różnymi architekturami komputera. Jeśli jednak kod zarządzany wywołuje natywne interfejsy API specyficzne dla platformy lub bibliotekę klas specyficznych dla platformy, będzie ona uruchamiana tylko w tym systemie operacyjnym.  
  
 Kompilacja JIT uwzględnia możliwość, że niektóre kodu nigdy nie może być wywoływana podczas wykonywania. Zamiast używać czasu i pamięci do konwertowania wszystkich MSIL w pliku PE do kodu macierzystego, konwertuje MSIL zgodnie z potrzebami podczas wykonywania i przechowuje wynikowy kod macierzysty w pamięci, dzięki czemu jest dostępny dla kolejnych wywołań w kontekście tego procesu. Moduł ładujący tworzy i dołącza skrótdo każdej metody w typie, gdy typ jest ładowany i inicjowany. Gdy metoda jest wywoływana po raz pierwszy, skrót przechodzi kontroli do kompilatora JIT, który konwertuje MSIL dla tej metody do kodu macierzystego i modyfikuje skrót, aby wskazać bezpośrednio do wygenerowanego kodu macierzystego. W związku z tym kolejne wywołania metody skompilowanej jit przejść bezpośrednio do kodu macierzystego.  
  
### <a name="install-time-code-generation-using-ngenexe"></a>Generowanie kodu czasu instalacji przy użyciu programu NGen.exe  
 Ponieważ kompilator JIT konwertuje msil zestawu do kodu macierzystego, gdy poszczególne metody zdefiniowane w tym zestawie są wywoływane, wpływa na wydajność niekorzystnie w czasie wykonywania. W większości przypadków ta zmniejszona wydajność jest dopuszczalna. Co ważniejsze kod generowany przez kompilator JIT jest powiązany z procesem, który wyzwolił kompilację. Nie można go udostępnić w wielu procesach. Aby umożliwić wygenerowany kod do współużytkowania przez wiele wywołań aplikacji lub w wielu procesach, które współużytkują zestaw zestawów, czas wykonywania języka wspólnego obsługuje tryb kompilacji z wyprzedzeniem. Ten tryb kompilacji z wyprzedzeniem używa [Ngen.exe (Native Image Generator)](../../docs/framework/tools/ngen-exe-native-image-generator.md) do konwersji zestawów MSIL do kodu macierzystego, podobnie jak kompilator JIT. Jednak działanie Ngen.exe różni się od działania kompilatora JIT na trzy sposoby:  
  
- Wykonuje konwersję z MSIL do kodu macierzystego przed uruchomieniem aplikacji, a nie podczas uruchamiania aplikacji.  
  
- Kompiluje cały zestaw w czasie, zamiast jednej metody naraz.  
  
- Utrzymuje wygenerowany kod w natywnej pamięci podręcznej obrazów jako plik na dysku.  
  
### <a name="code-verification"></a>Weryfikacja kodu  
 W ramach kompilacji do kodu macierzystego kod MSIL musi przejść proces weryfikacji, chyba że administrator ustanowił zasady zabezpieczeń, które umożliwia kod ominąć weryfikację. Weryfikacja sprawdza MSIL i metadane, aby dowiedzieć się, czy kod jest bezpieczny dla typu, co oznacza, że uzyskuje dostęp tylko do lokalizacji pamięci, do których jest autoryzowany. Bezpieczeństwo typów pomaga odizolować obiekty od siebie i pomaga chronić je przed nieumyślnym lub złośliwym uszkodzeniem. Zapewnia również pewność, że ograniczenia zabezpieczeń kodu mogą być niezawodnie egzekwowane.  
  
 Czas wykonywania opiera się na fakcie, że następujące instrukcje są prawdziwe dla kodu, który jest weryfikowalnie typu bezpieczne:  
  
- Odwołanie do typu jest ściśle zgodne z typem, do którego się odwołuje.  
  
- Tylko odpowiednio zdefiniowane operacje są wywoływane na obiekcie.  
  
- Tożsamości są tym, za co się podają.  
  
 Podczas procesu weryfikacji kod MSIL jest sprawdzany w celu potwierdzenia, że kod może uzyskać dostęp do lokalizacji pamięci i metod wywołania tylko za pośrednictwem poprawnie zdefiniowanych typów. Na przykład kod nie może zezwolić na dostęp do pól obiektu w sposób, który umożliwia przepełnienie lokalizacji pamięci. Ponadto weryfikacja sprawdza kod, aby ustalić, czy MSIL został poprawnie wygenerowany, ponieważ niepoprawne MSIL może prowadzić do naruszenia zasad bezpieczeństwa typu. Proces weryfikacji przekazuje dobrze zdefiniowany zestaw kodu bezpiecznego typu i przekazuje tylko kod, który jest bezpieczny dla typu. Jednak niektóre bezpieczne dla typu kodu może nie przejść weryfikacji z powodu pewnych ograniczeń procesu weryfikacji, a niektóre języki, zgodnie z projektem, nie produkują sprawdzalnie kodu bezpiecznego dla typu. Jeśli kod bezpieczny dla typu jest wymagany przez zasady zabezpieczeń, ale kod nie przekazuje weryfikacji, wyjątek jest zgłaszany po uruchomieniu kodu.  
  
 [Powrót do początku](#introduction)  
  
<a name="running_code"></a>
## <a name="running-code"></a>Uruchamianie kodu  
 Czas wykonywania języka wspólnego zapewnia infrastrukturę, która umożliwia wykonanie zarządzane odbywa ć i usług, które mogą być używane podczas wykonywania. Przed uruchomieniem metody należy ją skompilować do kodu specyficznego dla procesora. Każda metoda, dla której msil został wygenerowany jest Skompilowany JIT, gdy jest wywoływana po raz pierwszy, a następnie uruchom. Przy następnym uruchomieniu metody uruchamiany jest istniejący kod macierzysty skompilowany jit. Proces kompilacji JIT, a następnie uruchamiania kodu jest powtarzany do czasu zakończenia wykonywania.  
  
 Podczas wykonywania kod zarządzany odbiera usługi, takie jak wyrzucanie elementów bezużytecznych, zabezpieczenia, współdziałanie z kodem niezarządzanym, obsługa debugowania między językami oraz ulepszona obsługa wdrażania i wersji.  
  
 W systemie Microsoft Windows Vista moduł ładujący systemu operacyjnego sprawdza, czy moduły zarządzane są sprawdzane, sprawdzając nieco w nagłówku COFF. Bit jest ustawiony oznacza moduł zarządzany. Jeśli moduł ładujący wykryje moduły zarządzane, ładuje mscoree.dll i `_CorValidateImage` `_CorImageUnloading` powiadamia moduł ładujący, gdy obrazy modułu zarządzanego są ładowane i zwalniane. `_CorValidateImage`wykonuje następujące czynności:  
  
1. Zapewnia, że kod jest prawidłowy kod zarządzany.  
  
2. Zmienia punkt wejścia obrazu na punkt wejścia w czasie wykonywania.  
  
 W systemie Windows 64-bitowym obraz znajduje się w pamięci, `_CorValidateImage` przekształcając go z formatu PE32 na PE32+.  
  
 [Powrót do początku](#introduction)  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd](../../docs/framework/get-started/overview.md)
- [Niezależność od języka i składniki niezależne od języka](../../docs/standard/language-independence-and-language-independent-components.md)
- [Składniki samoopisujące się i metadane](../../docs/standard/metadata-and-self-describing-components.md)
- [Ilasm.exe (asembler IL)](../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Zabezpieczenia](../../docs/standard/security/index.md)
- [Współdziałanie z kodem niezarządzanym](../../docs/framework/interop/index.md)
- [Wdrożenie](../../docs/framework/deployment/net-framework-applications.md)
- [Zestawy w środowisku .NET](assembly/index.md)
- [Domeny aplikacji](../../docs/framework/app-domains/application-domains.md)
