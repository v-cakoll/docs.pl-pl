---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135606"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a>Składnia "Rozpocznij certyfikat zaufany" nie jest już obsługiwana dla certyfikatów głównych w systemie Linux

Certyfikaty główne w systemie Linux i inne systemy podobne do systemu UNIX (ale nie macOS) mogą być prezentowane w dwóch formach: standardowy `BEGIN CERTIFICATE` nagłówek PEM i nagłówek PEM `BEGIN TRUSTED CERTIFICATE` właściwy dla OpenSSL. Ostatnia składnia umożliwia dodatkową konfigurację, która spowodowała problemy ze zgodnością z <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> klasą platformy .NET Core. `BEGIN TRUSTED CERTIFICATE`zawartość certyfikatu głównego nie jest już ładowana przez aparat łańcucha, począwszy od platformy .NET Core 3,0.

#### <a name="change-description"></a>Zmień opis

Wcześniej zarówno składnie `BEGIN CERTIFICATE` , `BEGIN TRUSTED CERTIFICATE` jak i zostały użyte do wypełniania listy głównych relacji zaufania. Jeśli `BEGIN TRUSTED CERTIFICATE` składnia została użyta i w pliku określono dodatkowe opcje, <xref:System.Security.Cryptography.X509Certificates.X509Chain> mogło zostać zgłoszone, że zaufanie łańcucha zostało jawnie niedozwolone (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>). Jeśli jednak certyfikat został również określony ze `BEGIN CERTIFICATE` składnią w wcześniej załadowanym pliku, dozwolone jest zaufanie łańcucha.

Począwszy od platformy .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` , zawartość nie jest już odczytywana. Jeśli certyfikat nie jest również określony za pośrednictwem standardowej `BEGIN CERTIFICATE` składni, <xref:System.Security.Cryptography.X509Certificates.X509Chain> raporty, które nie są zaufane (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana nie ma wpływ na większość aplikacji, ale aplikacje, które nie mogą zobaczyć obu głównych źródeł certyfikatów z powodu problemów z uprawnieniami `UntrustedRoot` mogą wystąpić nieoczekiwane błędy po uaktualnieniu.

Wiele dystrybucji systemu Linux (lub dystrybucje) zapisywanie certyfikatów głównych w dwóch lokalizacjach: jeden certyfikat dla każdego pliku i jednoplikowego łączenia. W przypadku niektórych dystrybucje katalog z jednym certyfikatem jest stosowany `BEGIN TRUSTED CERTIFICATE` podczas łączenia plików przy użyciu standardowej `BEGIN CERTIFICATE` składni. Upewnij się, że wszystkie niestandardowe certyfikaty główne są `BEGIN CERTIFICATE` dodawane jako co najmniej jedna z tych lokalizacji, i że obie lokalizacje mogą być odczytywane przez aplikację.

Typowy katalog to */etc/SSL/certs/* , a typowy połączony plik to */etc/SSL/cert.pem*. Użyj polecenia `openssl version -d` , aby określić katalog główny specyficzny dla platformy, który może się różnić od */etc/SSL/*. Na przykład w systemie Ubuntu 18,04 katalog jest */usr/lib/SSL/certs/* , a plik jest */usr/lib/SSL/cert.pem*. Jednak */usr/lib/SSL/certs/* jest link symboliczny do */etc/SSL/certs/* i */usr/lib/SSL/cert.pem* nie istnieje.

```bash
$ openssl version -d
OPENSSLDIR: "/usr/lib/ssl"
$ ls -al /usr/lib/ssl
total 12
drwxr-xr-x  3 root root 4096 Dec 12 17:10 .
drwxr-xr-x 73 root root 4096 Feb 20 15:18 ..
lrwxrwxrwx  1 root root   14 Mar 27  2018 certs -> /etc/ssl/certs
drwxr-xr-x  2 root root 4096 Dec 12 17:10 misc
lrwxrwxrwx  1 root root   20 Nov 12 16:58 openssl.cnf -> /etc/ssl/openssl.cnf
lrwxrwxrwx  1 root root   16 Mar 27  2018 private -> /etc/ssl/private
```

### <a name="category"></a>Kategoria

Kryptografia

### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
