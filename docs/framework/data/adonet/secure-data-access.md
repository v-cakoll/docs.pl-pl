---
title: "Bezpieczny dostęp do danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 473ebd69-21a3-4627-b95e-4e04d035c56f
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c713cc8e5f3d7e81b196820e0a25fde0018b6c80
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="secure-data-access"></a>Bezpieczny dostęp do danych
Aby napisać bezpiecznego kodu ADO.NET, należy zapoznać mechanizmy zabezpieczeń dostępne w odpowiedni magazyn danych lub bazy danych. Należy również wziąć pod uwagę ryzyko związane z innych funkcji lub składniki, które mogą zawierać aplikacji.  
  
## <a name="authentication-authorization-and-permissions"></a>Uwierzytelnianie, autoryzację i uprawnień  
 Podczas łączenia z programem Microsoft SQL Server, używając uwierzytelniania systemu Windows, znanej także jako zintegrowanych zabezpieczeń, której ma zostać użyta tożsamość bieżącego aktywnego użytkownika systemu Windows, a nie przekazywanie identyfikator użytkownika i hasło. Zdecydowanie zalecane jest używanie uwierzytelniania systemu Windows, ponieważ poświadczenia użytkownika nie są widoczne w parametrach połączenia. Jeśli za pomocą uwierzytelniania systemu Windows nie może połączyć się z serwerem SQL, następnie należy rozważyć utworzenie parametry połączenia w czasie wykonywania za pomocą <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.  
  
 Poświadczenia używane do uwierzytelniania muszą być obsługiwane inaczej w zależności od typu aplikacji. Na przykład w aplikacji formularzy systemu Windows, monit o podanie informacji o uwierzytelnianiu użytkownika lub poświadczenia systemu Windows użytkownika mogą być używane. Jednak do aplikacji sieci Web, często uzyskuje dostęp do danych przy użyciu poświadczeń dostarczonych przez samą aplikację, a nie przez użytkownika.  
  
 Po uwierzytelnieniu użytkowników zakres ich działania jest zależna od przyznano uprawnienia do nich. Zawsze postępuj zgodnie z zasadą najniższych uprawnień i udzielić tylko te uprawnienia, które są absolutnie niezbędne.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)|Zawiera opis najlepszych rozwiązań dotyczących zabezpieczeń i techniki chroniące informacje dotyczące połączenia, na przykład szyfrowania parametrów połączenia za pomocą konfiguracji chronionych.|  
|[Zalecenia dotyczące strategii dostępu do danych](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)|Zawiera zalecenia dotyczące uzyskiwania dostępu do danych i wykonywanie operacji bazy danych.|  
|[Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md)|Zawiera opis sposobu tworzenia parametrów połączenia z danych wejściowych użytkownika w czasie wykonywania.|  
|[Przegląd zabezpieczeń serwera SQL](../../../../docs/framework/data/adonet/sql/overview-of-sql-server-security.md)|W tym artykule opisano architekturę zabezpieczeń programu SQL Server.|  
  
## <a name="parameterized-commands-and-sql-injection"></a>Sparametryzowanych poleceń i iniekcja kodu SQL  
 Za pomocą sparametryzowanych poleceń chroni przed atakami iniekcji kodu SQL, w których osoba atakująca "injects" polecenia w instrukcji SQL zabezpieczenia dokonywania na serwerze. Sparametryzowanych poleceń chronią przed ataku polegającego na iniekcji SQL, zapewniając, że wartości odebranych z zewnętrznego źródła są przekazywane jako tylko wartości i nie jest częścią instrukcji języka Transact-SQL. W związku z tym poleceń języka Transact-SQL do wartości nie są wykonywane w źródle danych. Zamiast są one oceniane wyłącznie jako wartość parametru. Oprócz zabezpieczeń zapewnianych sparametryzowanych poleceń zapewniają wygodną metodę organizowania wartości przekazane za pomocą instrukcji języka Transact-SQL lub procedury składowanej.  
  
 Aby uzyskać więcej informacji na temat używania sparametryzowanych poleceń zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Element DataAdapter parametrów](../../../../docs/framework/data/adonet/dataadapter-parameters.md)|Informacje dotyczące używania parametrów z `DataAdapter`.|  
|[Modyfikowanie danych w procedurach składowanych](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)|Opisuje sposób określić parametry i uzyskiwanie wartości zwracanej.|  
|[Zarządzanie uprawnieniami w procedurach składowanych w programie SQL Server](../../../../docs/framework/data/adonet/sql/managing-permissions-with-stored-procedures-in-sql-server.md)|Informacje dotyczące używania procedur składowanych serwera SQL w celu hermetyzacji dostępu do danych.|  
  
## <a name="script-exploits"></a>Luk w skryptach  
 Wykorzystać skryptu jest innej formy iniekcji używającej złośliwego znaków wstawione do strony sieci Web. Przeglądarka nie można zweryfikować wstawione znaki i będzie przetwarzać je jako część strony.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Przegląd luki w zabezpieczeniach skryptu](http://msdn.microsoft.com/library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07)|Opisuje sposób chronią przed skryptów i instrukcji SQL luki w zabezpieczeniach.|  
  
## <a name="probing-attacks"></a>Sondowanie ataków  
 Osoby atakujące często używają informacji z wyjątku, takie jak nazwa serwera, bazy danych lub tabeli, aby zainstalować ataku na system. Ponieważ wyjątków mogą zawierać określone informacje na temat aplikacji lub źródła danych, można zabezpieczyć źródła danych i aplikacji lepiej chroniony przez udostępnianie tylko istotnych informacji klientowi.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Podstawowe założenia obsługi wyjątków](../../../../docs/standard/exceptions/exception-handling-fundamentals.md)|Opisuje podstawowe formy Obsługa wyjątków strukturalnych try/catch/finally.|  
|[Najlepsze praktyki dotyczące wyjątków](../../../../docs/standard/exceptions/best-practices-for-exceptions.md)|Opis najlepszych rozwiązań do obsługi wyjątków.|  
  
## <a name="protecting-microsoft-access-and-excel-data-sources"></a>Ochrona programu Microsoft Access i źródeł danych  
 Programu Microsoft Access i Microsoft Excel może działać jako magazyn danych na potrzeby aplikacji ADO.NET, gdy wymagania dotyczące zabezpieczeń są minimalne lub nie istnieje. Ich funkcje zabezpieczeń dla przed intruzami, ale nie powinno być stosowane do więcej niż zniechęcić meddling przez użytkowników w organizacji uninformed. Pliki danych fizycznych dostępu i Excel istnieje w systemie plików, a musi być dostępny dla wszystkich użytkowników. Z tego powodu narażony na ataki, mogącymi skutkować kradzieżą lub utraty danych, ponieważ pliki można łatwo skopiować lub zmodyfikować. Gdy wymagana jest niezawodna zabezpieczeń, użyj programu SQL Server lub innej bazy danych na serwerze której pliki danych fizycznych nie są do odczytu z systemu plików.  
  
 Aby uzyskać więcej informacji dotyczących ochrony danych programu Access i Excel zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Zagadnienia dotyczące zabezpieczeń i wskazówki dotyczące Access 2007](http://go.microsoft.com/fwlink/?LinkId=98354)|Opisuje metody zabezpieczeń Access 2007, takie szyfrowania plików, administrowania hasła Konwertowanie bazy danych na nowy format ACCDB i ACCDE i korzystanie z innych opcji zabezpieczeń.|  
|[Ochrona dostępu do bazy danych z zabezpieczeń na poziomie użytkownika (MDB)](http://go.microsoft.com/fwlink/?LinkId=47697)|Dotyczy 2003 dostępu. Zawiera instrukcje dotyczące wdrażania zabezpieczeń na poziomie użytkownika do ochrony danych w programie Access 2003.|  
|[Opis roli pliki z informacjami o grupie roboczej w zabezpieczenia dostępu](http://support.microsoft.com/kb/305542)|W zabezpieczenia 2003 dostęp wyjaśniono roli i relacji tego pliku.|  
|[Często zadawane pytania dotyczące zabezpieczeń firmy Microsoft dostęp dla programu Microsoft Access w wersji 2.0 za pomocą 2000](http://go.microsoft.com/fwlink/?LinkId=47698)|W wersji do pobrania firmy Microsoft dostęp zabezpieczeń często zadawane pytania.|  
|[Rozwiązywanie problemów dotyczących zabezpieczeń i ochrony](http://go.microsoft.com/fwlink/?LinkId=47703)|Przedstawia informacje o rozwiązania typowych problemów z zabezpieczeniami w programie Excel 2003.|  
  
## <a name="enterprise-services"></a>Usługi w przedsiębiorstwie  
 COM + zawiera własną model zabezpieczeń, który polega na konta systemu Windows NT i personifikacji procesu/wątku. <xref:System.EnterpriseServices> Przestrzeń nazw zawiera otoki, umożliwiających aplikacjom .NET integracji kodu zarządzanego z zabezpieczeń usług COM + za pośrednictwem <xref:System.EnterpriseServices.ServicedComponent> klasy.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[COM + opartej na rolach zabezpieczeń i .NET Framework](http://msdn.microsoft.com/en-us/02ab22ef-e5e2-4d29-b33a-6e03d94c4981)|W tym artykule omówiono sposobu integracji z usługami zabezpieczeń COM + kodu zarządzanego.|  
  
## <a name="interoperating-with-unmanaged-code"></a>Współdziałanie z kodem niezarządzanym  
 .NET Framework zapewnia do interakcji z kodem niezarządzanym, w tym modelu COM składników, COM + usług, bibliotek typu zewnętrznego i wiele usług systemu operacyjnego. Praca z kodem niezarządzanym obejmuje będzie zewnątrz zabezpieczeń dla zarządzanego kodu. Zarówno w kodzie, jak i każdy kod wywołujący go musi mieć niezarządzanych uprawnień kodu (<xref:System.Security.Permissions.SecurityPermission> z <xref:System.Security.Permissions.SecurityPermissionFlag.UnmanagedCode> określona flaga). Niezarządzany kod można wprowadzać luk w zabezpieczeniach niezamierzone do aplikacji. W związku z tym należy unikać współdziałanie z kodem niezarządzanym, chyba że jest bezwzględnie konieczne.  
  
 Aby uzyskać więcej informacji zobacz następujące zasoby.  
  
|Zasób|Opis|  
|--------------|-----------------|  
|[Współdziałanie z kodem niezarządzanym](../../../../docs/framework/interop/index.md)|Zawiera tematów opisujących sposób udostępnianie składników modelu COM aplikacji .NET Framework i udostępnianie składników .NET Framework modelowi COM.|  
|[Współdziałanie COM zaawansowane](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)|Zawiera tematy zaawansowane, takie jak podstawowe zestawy międzyoperacyjne, wątków i przekazywanie niestandardowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ADO.NET](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [Zabezpieczenia serwera SQL](../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 [Zalecenia dotyczące strategii dostępu do danych](http://msdn.microsoft.com/en-us/72411f32-d12a-4de8-b961-e54fca7faaf5)  
 [Ochrona informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 [Konstruktorzy ciągów połączenia](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
