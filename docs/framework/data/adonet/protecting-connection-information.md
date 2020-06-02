---
title: Ochrona informacji o połączeniu
description: Informacje na temat luk w zabezpieczeniach w ciągach połączeń, które mogą być spowodowane sposobem konstruowania i utrwalania parametrów połączenia oraz typem uwierzytelniania.
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 0e693fd99384a2808a621b358f8e70c6777c3930
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286653"
---
# <a name="protecting-connection-information"></a>Ochrona informacji o połączeniu
Ochrona dostępu do źródła danych jest jednym z najważniejszych celów związanych z zabezpieczaniem aplikacji. Parametry połączenia przedstawiają potencjalną lukę w zabezpieczeniach, jeśli nie została zabezpieczona. Przechowywanie informacji o połączeniu w postaci zwykłego tekstu lub utrwalanie ich w pamięci podnoszącej ryzyko złamania całego systemu. Parametry połączenia osadzone w kodzie źródłowym mogą zostać odczytane przy użyciu [Ildasm. exe (Il dezasembler)](../../tools/ildasm-exe-il-disassembler.md) do wyświetlania języka pośredniego firmy Microsoft (MSIL) w skompilowanym zestawie.  
  
 Luki w zabezpieczeniach dotyczące parametrów połączenia mogą powstać w zależności od używanego typu uwierzytelniania, sposobu utrwalania ciągów połączenia w pamięci i na dysku oraz technik używanych do konstruowania ich w czasie wykonywania.  
  
## <a name="use-windows-authentication"></a>Użyj uwierzytelniania systemu Windows  
 Aby ograniczyć dostęp do źródła danych, należy zabezpieczyć informacje dotyczące połączenia, takie jak identyfikator użytkownika, hasło i nazwa źródła danych. Aby uniknąć udostępniania informacji o użytkowniku, zalecamy używanie uwierzytelniania systemu Windows (nazywanego czasem *zabezpieczeniami zintegrowanymi*) wszędzie tam, gdzie to możliwe. Uwierzytelnianie systemu Windows jest określone w parametrach połączenia przy użyciu `Integrated Security` `Trusted_Connection` słów kluczowych lub, eliminując konieczność używania identyfikatora użytkownika i hasła. W przypadku korzystania z uwierzytelniania systemu Windows użytkownicy są uwierzytelniani przez system Windows, a dostęp do zasobów serwera i bazy danych jest określany przez przyznanie uprawnień użytkownikom i grupom systemu Windows.  
  
 W sytuacjach, gdy nie jest możliwe korzystanie z uwierzytelniania systemu Windows, należy użyć dodatkowej opieki, ponieważ poświadczenia użytkownika są ujawniane w parametrach połączenia. W aplikacji ASP.NET można skonfigurować konto systemu Windows jako stałą tożsamość, która jest używana do łączenia się z bazami danych i innymi zasobami sieciowymi. Należy włączyć personifikację w elemencie Identity w pliku **Web. config** i określić nazwę użytkownika i hasło.  
  
```xml  
<identity impersonate="true"
        userName="MyDomain\UserAccount"
        password="*****" />  
```  
  
 Stałe konto tożsamości powinno być kontem z niskimi uprawnieniami, które ma przyznane tylko niezbędne uprawnienia w bazie danych. Ponadto należy zaszyfrować plik konfiguracji, aby nazwa użytkownika i hasło nie były ujawniane w postaci zwykłego tekstu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Nie używaj plików Universal Data Link (UDL)  
 Należy unikać zapisywania parametrów połączenia dla elementu <xref:System.Data.OleDb.OleDbConnection> w pliku Universal Data Link (UDL). UDL są przechowywane w postaci zwykłego tekstu i nie mogą być szyfrowane. Plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji i nie może być zabezpieczony ani szyfrowany przy użyciu .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Unikanie ataków iniekcji przy użyciu konstruktorów parametrów połączenia  
 Atak polegający na iniekcji parametrów połączenia może wystąpić, gdy dynamiczne łączenie ciągów służy do tworzenia parametrów połączenia na podstawie danych wejściowych użytkownika. Jeśli dane wejściowe użytkownika nie są zweryfikowane i złośliwy tekst lub znaki nie zostały zmienione, osoba atakująca może uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Aby rozwiązać ten problem, ADO.NET 2,0 wprowadził nowe klasy konstruktora parametrów połączenia w celu zweryfikowania składni parametrów połączenia i upewnienia się, że nie wprowadzono dodatkowych parametrów. Aby uzyskać więcej informacji, zobacz [konstruktory parametrów połączenia](connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Użyj informacji o zabezpieczeniach utrwalania = FAŁSZ  
 Wartość domyślna dla `Persist Security Info` ma wartość false. Zalecamy używanie tego ustawienia domyślnego we wszystkich parametrach połączenia. Ustawienie `Persist Security Info` na `true` lub `yes` dopuszcza informacje dotyczące zabezpieczeń, w tym identyfikator użytkownika i hasło, które zostaną uzyskane z połączenia po jego otwarciu. Gdy `Persist Security Info` jest ustawiona na `false` lub `no` , informacje o zabezpieczeniach są odrzucane po użyciu do otwarcia połączenia, co zapewnia, że niezaufane źródło nie ma dostępu do informacji poufnych z uwzględnieniem zabezpieczeń.  
  
## <a name="encrypt-configuration-files"></a>Szyfruj pliki konfiguracji  
 Możesz również przechowywać parametry połączenia w plikach konfiguracyjnych, co eliminuje konieczność osadzania ich w kodzie aplikacji. Pliki konfiguracji to standardowe pliki XML, dla których .NET Framework definiuje wspólny zestaw elementów. Parametry połączenia w plikach konfiguracyjnych są zwykle przechowywane wewnątrz **\<connectionStrings>** elementu w pliku **App. config** dla aplikacji systemu Windows lub **Web. config** dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat podstaw przechowywania, pobierania i szyfrowania parametrów połączenia z plików konfiguracji, zobacz [parametry połączeń i pliki konfiguracji](connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Szyfrowanie informacji o konfiguracji przy użyciu konfiguracji chronionej](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Zabezpieczenia w .NET](../../../standard/security/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
