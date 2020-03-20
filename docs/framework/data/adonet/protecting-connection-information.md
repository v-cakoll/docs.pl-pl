---
title: Ochrona informacji o połączeniu
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 1039d3fd797a16391876b59aa018b30b7f397aeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149222"
---
# <a name="protecting-connection-information"></a>Ochrona informacji o połączeniu
Ochrona dostępu do źródła danych jest jednym z najważniejszych celów podczas zabezpieczania aplikacji. Parametry połączenia stanowią potencjalną lukę w zabezpieczeniach, jeśli nie są zabezpieczone. Przechowywanie informacji o połączeniu w postaci zwykłego tekstu lub utrwalanie ich w pamięci może na szwank całego systemu. Parametry połączenia osadzone w kodzie źródłowym można odczytać za pomocą [programu Ildasm.exe (IL Disassembler)](../../tools/ildasm-exe-il-disassembler.md) w celu wyświetlenia języka pośredniego firmy Microsoft (MSIL) w skompilowanym zestawie.  
  
 Luki w zabezpieczeniach związane z ciągami połączeń mogą powstać na podstawie typu używanego uwierzytelniania, sposobu utrwalenia ciągów połączeń w pamięci i na dysku oraz technik używanych do konstruowania ich w czasie wykonywania.  
  
## <a name="use-windows-authentication"></a>Użyj uwierzytelniania systemu Windows  
 Aby ograniczyć dostęp do źródła danych, należy zabezpieczyć informacje o połączeniu, takie jak identyfikator użytkownika, hasło i nazwa źródła danych. Aby uniknąć ujawniania informacji o użytkowniku, zalecamy użycie uwierzytelniania systemu Windows (czasami określanego jako *zintegrowane zabezpieczenia),* jeśli to możliwe. Uwierzytelnianie systemu Windows jest określone `Integrated Security` w `Trusted_Connection` ciągu połączenia przy użyciu lub słów kluczowych, eliminując konieczność używania identyfikatora użytkownika i hasła. Podczas korzystania z uwierzytelniania systemu Windows użytkownicy są uwierzytelniane przez system Windows, a dostęp do zasobów serwera i bazy danych jest określany przez przyznanie uprawnień użytkownikom i grupom systemu Windows.  
  
 W sytuacjach, w których nie jest możliwe użycie uwierzytelniania systemu Windows, należy użyć dodatkowej starannością, ponieważ poświadczenia użytkownika są widoczne w ciągu połączenia. W aplikacji ASP.NET można skonfigurować konto systemu Windows jako stałą tożsamość używaną do łączenia się z bazami danych i innymi zasobami sieciowymi. Włącz personifikację w elemencie tożsamości w pliku **web.config** i określisz nazwę użytkownika i hasło.  
  
```xml  
<identity impersonate="true"
        userName="MyDomain\UserAccount"
        password="*****" />  
```  
  
 Konto tożsamości stałej powinno być kontem o niskich uprawnieniach, któremu przyznano tylko niezbędne uprawnienia w bazie danych. Ponadto należy zaszyfrować plik konfiguracyjny, tak aby nazwa użytkownika i hasło nie były widoczne w postaci zwykłego tekstu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Nie używaj plików Universal Data Link (UDL)  
 Należy unikać przechowywania ciągów <xref:System.Data.OleDb.OleDbConnection> połączeń dla pliku uniwersalnego łącza danych (UDL). Listy UDL są przechowywane w postaci zwykłego tekstu i nie mogą być szyfrowane. Plik UDL jest zewnętrznym zasobem opartym na plikach dla aplikacji i nie może być zabezpieczony ani zaszyfrowany za pomocą programu .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Unikaj ataków wtryskowych za pomocą konstruktorów ciągów połączeń  
 Atak iniekcji ciągu połączenia może wystąpić, gdy dynamiczne łączenie ciągów jest używane do tworzenia ciągów połączeń na podstawie danych wejściowych użytkownika. Jeśli dane wejściowe użytkownika nie zostaną zweryfikowane, a złośliwy tekst lub znaki nie zostaną zmienione, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Aby rozwiązać ten problem, ADO.NET 2.0 wprowadziła nowe klasy konstruktora ciągów połączeń, aby sprawdzić poprawność składni ciągu połączenia i upewnić się, że dodatkowe parametry nie zostaną wprowadzone. Aby uzyskać więcej informacji, zobacz [Konstruktorzy ciągów połączeń](connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Użyj funkcji Utrwalanie informacji zabezpieczających=Fałsz  
 Wartość domyślna `Persist Security Info` jest false; zalecamy użycie tej wartości domyślnej we wszystkich ciągach połączeń. Ustawienie `Persist Security Info` `true` lub `yes` umożliwia uzyskanie informacji wrażliwych na zabezpieczenia, w tym identyfikatora użytkownika i hasła, z połączenia po ich otwarciu. Gdy `Persist Security Info` jest `false` ustawiona lub `no`, informacje zabezpieczające są odrzucane po ich użyciu do otwarcia połączenia, zapewniając, że niezaufane źródło nie ma dostępu do informacji poufnych zabezpieczeń.  
  
## <a name="encrypt-configuration-files"></a>Szyfruj pliki konfiguracyjne  
 Można również przechowywać parametry połączenia w plikach konfiguracyjnych, co eliminuje konieczność osadzania ich w kodzie aplikacji. Pliki konfiguracyjne są standardowymi plikami XML, dla których program .NET Framework zdefiniował wspólny zestaw elementów. Parametry połączenia w plikach konfiguracyjnych są zazwyczaj przechowywane wewnątrz ** \<connectionStrings>** element w **app.config** dla aplikacji systemu Windows lub pliku **web.config** dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat podstaw przechowywania, pobierania i szyfrowania ciągów połączeń z plików konfiguracyjnych, zobacz [Parametry połączenia i pliki konfiguracyjne](connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Zobacz też

- [Zabezpieczanie aplikacji ADO.NET](securing-ado-net-applications.md)
- [Szyfrowanie informacji o konfiguracji przy użyciu chronionej konfiguracji](https://docs.microsoft.com/previous-versions/aspnet/53tyfkaw(v=vs.100))
- [Zabezpieczenia w .NET](../../../standard/security/index.md)
- [Omówienie ADO.NET](ado-net-overview.md)
