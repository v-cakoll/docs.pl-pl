---
title: Ochrona informacji o połączeniu
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 4cf503af6f57eefb0990a8e7e728ea5c1474bfa7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363354"
---
# <a name="protecting-connection-information"></a>Ochrona informacji o połączeniu
Ochrona dostępu do źródła danych jest jednym z najważniejszych celów zabezpieczania aplikacji. Ciąg połączenia przedstawia potencjalne luki w zabezpieczeniach, jeśli nie jest zabezpieczony. Przechowywanie informacji o połączeniu w formacie zwykłego tekstu lub utrwalanie go w pamięci ryzyko naruszenia całego systemu. Osadzone w kodzie źródłowym parametry połączenia mogą być odczytywane przy użyciu [Ildasm.exe (dezasembler IL)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić język pośredni firmy Microsoft (MSIL) w skompilowanym zestawie.  
  
 Luki w zabezpieczeniach, które mogą wystąpić obejmujące parametry połączenia oparte na typ uwierzytelniania używany, jak parametry połączenia są zachowywane w pamięci i na dysku i techniki tworzenia ich w czasie wykonywania.  
  
## <a name="use-windows-authentication"></a>Uwierzytelnianie systemu Windows  
 Ułatwia ograniczenie dostępu do źródła danych, należy zabezpieczyć połączenie informacje takie jak nazwa źródła identyfikator, hasło i danych użytkownika. Aby uniknąć udostępnianie informacji o użytkowniku, zalecane jest używanie uwierzytelniania systemu Windows (czasami zwanej *zabezpieczenia zintegrowane*) tam gdzie to możliwe. Uwierzytelnianie systemu Windows określono w parametrach połączenia przy użyciu `Integrated Security` lub `Trusted_Connection` słów kluczowych, eliminując konieczność użycia identyfikator użytkownika i hasło. Podczas korzystania z uwierzytelniania systemu Windows, użytkownicy są uwierzytelniani przez system Windows i dostęp do zasobów serwera i bazy danych jest określany przez udzielanie uprawnień dla użytkowników systemu Windows i grup.  
  
 W sytuacjach, gdy nie jest możliwe do uwierzytelniania systemu Windows należy użyć szczególną uwagę, ponieważ poświadczenia użytkownika są widoczne w parametrach połączenia. W aplikacji ASP.NET można skonfigurować konta systemu Windows jako tożsamości stałej, która służy do nawiązania połączenia bazy danych i innych zasobów sieciowych. Włączanie personifikacji w tożsamości elementu w **web.config** pliku i określ nazwę użytkownika i hasło.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Konto tożsamości stałej powinno być konto niskich uprawnieniach, które zostały przyznane tylko niezbędne uprawnienia w bazie danych. Ponadto należy szyfrowania pliku konfiguracji, tak, aby nazwy użytkownika i hasła nie są widoczne w postaci zwykłego tekstu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Czy nie Użyj Universal Data Link () pliki UDL  
 Nie należy przechowywać parametry połączenia dla <xref:System.Data.OleDb.OleDbConnection> w plik Universal Data Link (UDL). UDL są przechowywane w postaci zwykłego tekstu i nie mogą być szyfrowane. Plik UDL jest zewnętrzny zasób opartych na plikach do aplikacji, i nie mogą być chronione ani zaszyfrowane za pomocą programu .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Unikaj ataków iniekcji z konstruktorów ciąg połączenia  
 Atak iniekcji ciągu połączenia może wystąpić, gdy dynamiczne ciągów jest używany do tworzenia parametry połączenia oparte na danych wejściowych użytkownika. Jeśli dane wejściowe użytkownika nie jest zweryfikowany i złośliwych tekst lub znaków, które nie miały zmienione znaczenie, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Aby rozwiązać ten problem, ADO.NET 2.0 wprowadzono nowe połączenie ciąg konstruktora klasy do sprawdzania poprawności składnia ciągu połączenia i upewnij się, że nie wprowadzono dodatkowe parametry. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Użyj Utrzymuj informacje o zabezpieczeniach = False  
 Wartość domyślna dla `Persist Security Info` ma wartość FAŁSZ; zaleca się używanie to ustawienie domyślne w wszystkie parametry połączenia. Ustawienie `Persist Security Info` do `true` lub `yes` umożliwia informacji istotnych dla zabezpieczeń, w tym nazwę użytkownika i hasło, które mają zostać uzyskane z połączenia po jej otwarciu. Gdy `Persist Security Info` ustawiono `false` lub `no`, informacje o zabezpieczeniach są usuwane po jest używany do otwierania połączenia zapewnienie, że niezaufanego źródła nie ma dostępu do informacji poufnych.  
  
## <a name="encrypt-configuration-files"></a>Szyfrowanie plików konfiguracji  
 Można przechowywać parametry połączenia w plikach konfiguracji, która eliminuje potrzebę osadzić je w kodzie aplikacji. Pliki konfiguracji są standardowe pliki XML, dla których programu .NET Framework został zdefiniowany zestaw wspólnych elementów. Parametry połączenia w plikach konfiguracji są zwykle przechowywane wewnątrz  **\<connectionStrings >** element **app.config** dla aplikacji systemu Windows lub  **plik Web.config** plików dla aplikacji ASP.NET. Aby uzyskać więcej informacji na podstawowe informacje dotyczące przechowywania, pobieranie i szyfrowania parametrów połączenia z plików konfiguracyjnych, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Szyfrowanie za pomocą konfiguracji chronionych informacji o konfiguracji](http://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [Pave – zabezpieczeń w trybie macierzystym i kodu platformy .NET Framework](http://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
