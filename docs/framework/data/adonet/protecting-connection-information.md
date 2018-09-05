---
title: Ochrona informacji o połączeniu
ms.date: 03/30/2017
ms.assetid: 1471f580-bcd4-4046-bdaf-d2541ecda2f4
ms.openlocfilehash: 6cd27f2bce1879301e80c7a8ec689971705a45b0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513480"
---
# <a name="protecting-connection-information"></a>Ochrona informacji o połączeniu
Ochrona dostępu do źródła danych jest jednym z najważniejszych celów podczas zabezpieczania aplikacji. Parametry połączenia przedstawia informacje o potencjalnych luk w zabezpieczeniach, jeśli nie jest zabezpieczony. Przechowywanie informacji o połączeniu w postaci zwykłego tekstu lub utrwalanie go w pamięci ryzyko obniżania całego systemu. Parametry połączenia osadzone w kodzie źródłowym, może zostać odczytany przy użyciu [Ildasm.exe (dezasembler IL)](../../../../docs/framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić składnię języka Microsoft intermediate language (MSIL) w skompilowanym zestawie.  
  
 Luki w zabezpieczeniach który obejmujące parametry połączenia mogą wystąpić na podstawie typu uwierzytelniania używane, jak parametry połączenia są zachowywane w pamięci i na dysku i techniki penetracji sieci używane do konstruowania je w czasie wykonywania.  
  
## <a name="use-windows-authentication"></a>Uwierzytelnianie Windows  
 Aby ułatwić dostęp do źródła danych, należy zabezpieczyć informacje o połączeniu, takie jak nazwa źródłowego Identyfikatora, hasła i dane użytkownika. Aby uniknąć ujawnienia informacji o użytkowniku, zaleca się korzystania z uwierzytelniania Windows (czasami określane jako *zintegrowane zabezpieczenia*) wszędzie tam, gdzie to możliwe. Uwierzytelnianie Windows określono w parametrach połączenia przy użyciu `Integrated Security` lub `Trusted_Connection` słów kluczowych, eliminując konieczność łączenia się przy użyciu Identyfikatora użytkownika i hasło. Korzystając z uwierzytelniania Windows, użytkownicy są uwierzytelniani przez Windows, a dostęp do zasobów serwera i bazy danych jest określona, przyznając uprawnienia Windows użytkowników i grup.  
  
 W sytuacjach, w którym nie jest możliwe do korzystania z uwierzytelniania Windows należy użyć szczególną ostrożność należy zachować, ponieważ poświadczenia użytkownika są widoczne w parametrach połączenia. W aplikacji ASP.NET można skonfigurować również konto Windows jako stały tożsamości, która służy do łączenia się z bazami danych i innych zasobów sieciowych. Włączanie personifikacji w elemencie tożsamości w **web.config** plik i określ nazwę użytkownika i hasło.  
  
```xml  
<identity impersonate="true"   
        userName="MyDomain\UserAccount"   
        password="*****" />  
```  
  
 Konto tożsamości stałej powinno być konta o niskim poziomie uprawnień, które zostały udzielone tylko niezbędne uprawnienia w bazie danych. Ponadto należy szyfrowania pliku konfiguracji, tak, aby nazwy użytkownika i hasła nie są widoczne w postaci zwykłego tekstu.  
  
## <a name="do-not-use-universal-data-link-udl-files"></a>Czy pliki nie Użyj Universal Data Link (UDL)  
 Nie należy przechowywać parametry połączenia dla <xref:System.Data.OleDb.OleDbConnection> w pliku Universal Data Link (UDL). UDL są przechowywane w postaci zwykłego tekstu i nie może być szyfrowana. Plik UDL jest oparte na plikach zasób zewnętrzny do aplikacji i nie mogą być chronione ani zaszyfrowane za pomocą programu .NET Framework.  
  
## <a name="avoid-injection-attacks-with-connection-string-builders"></a>Należy unikać ataki przez iniekcję kodu z Konstruktorzy parametrów połączeń  
 Ataku polegającego na iniekcji ciąg połączenia może wystąpić, gdy dynamiczne ciągów jest używany do tworzenia parametrów połączenia, w oparciu o dane wejściowe użytkownika. Jeśli dane wejściowe użytkownika nie jest tekst zweryfikowane i złośliwych lub znaków, nie zawiera wyjścia, osoba atakująca może potencjalnie uzyskać dostęp do poufnych danych lub innych zasobów na serwerze. Aby rozwiązać ten problem, ADO.NET w wersji 2.0 wprowadzono nowe klasy konstruktora parametrów połączenia do sprawdzania poprawności składnia ciągu połączenia i upewnij się, że nie wprowadzono dodatkowe parametry. Aby uzyskać więcej informacji, zobacz [Konstruktorzy parametrów połączeń](../../../../docs/framework/data/adonet/connection-string-builders.md).  
  
## <a name="use-persist-security-infofalse"></a>Użyj Utrwal informacje zabezpieczające = False  
 Wartością domyślną dla `Persist Security Info` ma wartość FAŁSZ; w zalecamy używanie tego ustawienia domyślnego wszystkie parametry połączenia. Ustawienie `Persist Security Info` do `true` lub `yes` umożliwia informacje związane z zabezpieczeniami, w tym nazwę użytkownika i hasło, które mają zostać uzyskane z połączenia po jego otwarciu. Gdy `Persist Security Info` ustawiono `false` lub `no`, informacje o zabezpieczeniach są usuwane po jest używany do otwierania połączenia, zapewniając, że niezaufanego źródła nie ma dostępu do informacji poufnych.  
  
## <a name="encrypt-configuration-files"></a>Szyfrowanie plików konfiguracji  
 Można również przechowywać parametry połączenia w plikach konfiguracji, więc nie trzeba ich osadzać w kodzie twojej aplikacji. Pliki konfiguracyjne są standardowymi plikami XML, dla których programu .NET Framework został zdefiniowany zestaw wspólnych elementów. Parametry połączenia w plikach konfiguracji są zazwyczaj przechowywane wewnątrz  **\<connectionStrings >** element **app.config** dla aplikacji Windows, lub  **plik Web.config** plików dla aplikacji ASP.NET. Aby uzyskać więcej informacji na temat przechowywania, pobieranie i szyfrowania parametrów połączenia z plików konfiguracji, zobacz [parametry połączenia i pliki konfiguracyjne](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Szyfrowanie przy użyciu konfiguracji chronionych informacji o konfiguracji](https://msdn.microsoft.com/library/51cdfe5b-9d82-458c-94ff-c551c4f38ed1)  
 [PAVE zabezpieczeń w natywnym i kodzie .NET Framework](https://msdn.microsoft.com/library/bd61be84-c143-409a-a75a-44253724f784)  
 [ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych](https://go.microsoft.com/fwlink/?LinkId=217917)
