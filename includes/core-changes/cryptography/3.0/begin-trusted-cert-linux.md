---
ms.openlocfilehash: 1d9a5bbea49730ee6cf99eaae6b20a0035e70b97
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135606"
---
### <a name="begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux"></a><span data-ttu-id="cda18-101">Składnia "Rozpocznij certyfikat zaufany" nie jest już obsługiwana dla certyfikatów głównych w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="cda18-101">"BEGIN TRUSTED CERTIFICATE" syntax no longer supported for root certificates on Linux</span></span>

<span data-ttu-id="cda18-102">Certyfikaty główne w systemie Linux i inne systemy podobne do systemu UNIX (ale nie macOS) mogą być prezentowane w dwóch formach: standardowy `BEGIN CERTIFICATE` nagłówek PEM i nagłówek PEM `BEGIN TRUSTED CERTIFICATE` właściwy dla OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="cda18-102">Root certificates on Linux and other Unix-like systems (but not macOS) can be presented in two forms: the standard `BEGIN CERTIFICATE` PEM header, and the OpenSSL-specific `BEGIN TRUSTED CERTIFICATE` PEM header.</span></span> <span data-ttu-id="cda18-103">Ostatnia składnia umożliwia dodatkową konfigurację, która spowodowała problemy ze zgodnością z <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> klasą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cda18-103">The latter syntax allows for additional configuration that has caused compatibility issues with .NET Core's <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName> class.</span></span> <span data-ttu-id="cda18-104">`BEGIN TRUSTED CERTIFICATE`zawartość certyfikatu głównego nie jest już ładowana przez aparat łańcucha, począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="cda18-104">`BEGIN TRUSTED CERTIFICATE` root certificate contents are no longer loaded by the chain engine starting in .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="cda18-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="cda18-105">Change description</span></span>

<span data-ttu-id="cda18-106">Wcześniej zarówno składnie `BEGIN CERTIFICATE` , `BEGIN TRUSTED CERTIFICATE` jak i zostały użyte do wypełniania listy głównych relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="cda18-106">Previously, both the `BEGIN CERTIFICATE` and `BEGIN TRUSTED CERTIFICATE` syntaxes were used to populate the root trust list.</span></span> <span data-ttu-id="cda18-107">Jeśli `BEGIN TRUSTED CERTIFICATE` składnia została użyta i w pliku określono dodatkowe opcje, <xref:System.Security.Cryptography.X509Certificates.X509Chain> mogło zostać zgłoszone, że zaufanie łańcucha zostało jawnie niedozwolone (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="cda18-107">If the `BEGIN TRUSTED CERTIFICATE` syntax was used and additional options were specified in the file, <xref:System.Security.Cryptography.X509Certificates.X509Chain> may have reported that the chain trust was explicitly disallowed (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.ExplicitDistrust?displayProperty=nameWithType>).</span></span> <span data-ttu-id="cda18-108">Jeśli jednak certyfikat został również określony ze `BEGIN CERTIFICATE` składnią w wcześniej załadowanym pliku, dozwolone jest zaufanie łańcucha.</span><span class="sxs-lookup"><span data-stu-id="cda18-108">However, if the certificate was also specified with the `BEGIN CERTIFICATE` syntax in a previously loaded file, the chain trust was allowed.</span></span>

<span data-ttu-id="cda18-109">Począwszy od platformy .NET Core 3,0 `BEGIN TRUSTED CERTIFICATE` , zawartość nie jest już odczytywana.</span><span class="sxs-lookup"><span data-stu-id="cda18-109">Starting in .NET Core 3.0, `BEGIN TRUSTED CERTIFICATE` contents are no longer read.</span></span> <span data-ttu-id="cda18-110">Jeśli certyfikat nie jest również określony za pośrednictwem standardowej `BEGIN CERTIFICATE` składni, <xref:System.Security.Cryptography.X509Certificates.X509Chain> raporty, które nie są zaufane (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="cda18-110">If the certificate is not also specified via a standard `BEGIN CERTIFICATE` syntax, the <xref:System.Security.Cryptography.X509Certificates.X509Chain> reports that the root is not trusted (<xref:System.Security.Cryptography.X509Certificates.X509ChainStatusFlags.UntrustedRoot?displayProperty=nameWithType>).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cda18-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cda18-111">Version introduced</span></span>

<span data-ttu-id="cda18-112">3.0</span><span class="sxs-lookup"><span data-stu-id="cda18-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cda18-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cda18-113">Recommended action</span></span>

<span data-ttu-id="cda18-114">Ta zmiana nie ma wpływ na większość aplikacji, ale aplikacje, które nie mogą zobaczyć obu głównych źródeł certyfikatów z powodu problemów z uprawnieniami `UntrustedRoot` mogą wystąpić nieoczekiwane błędy po uaktualnieniu.</span><span class="sxs-lookup"><span data-stu-id="cda18-114">Most applications are unaffected by this change, but applications that cannot see both root certificate sources because of permissions problems may experience unexpected `UntrustedRoot` errors after upgrading.</span></span>

<span data-ttu-id="cda18-115">Wiele dystrybucji systemu Linux (lub dystrybucje) zapisywanie certyfikatów głównych w dwóch lokalizacjach: jeden certyfikat dla każdego pliku i jednoplikowego łączenia.</span><span class="sxs-lookup"><span data-stu-id="cda18-115">Many Linux distributions (or distros) write root certificates into two locations: a one-certificate-per-file directory, and a one-file concatenation.</span></span> <span data-ttu-id="cda18-116">W przypadku niektórych dystrybucje katalog z jednym certyfikatem jest stosowany `BEGIN TRUSTED CERTIFICATE` podczas łączenia plików przy użyciu standardowej `BEGIN CERTIFICATE` składni.</span><span class="sxs-lookup"><span data-stu-id="cda18-116">On some distros, the one-certificate-per-file directory uses the `BEGIN TRUSTED CERTIFICATE` syntax while the file concatenation uses the standard `BEGIN CERTIFICATE` syntax.</span></span> <span data-ttu-id="cda18-117">Upewnij się, że wszystkie niestandardowe certyfikaty główne są `BEGIN CERTIFICATE` dodawane jako co najmniej jedna z tych lokalizacji, i że obie lokalizacje mogą być odczytywane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="cda18-117">Ensure that any custom root certificates are added as `BEGIN CERTIFICATE` in at least one of these locations, and that both locations can be read by your application.</span></span>

<span data-ttu-id="cda18-118">Typowy katalog to */etc/SSL/certs/* , a typowy połączony plik to */etc/SSL/cert.pem*.</span><span class="sxs-lookup"><span data-stu-id="cda18-118">The typical directory is */etc/ssl/certs/* and the typical concatenated file is */etc/ssl/cert.pem*.</span></span> <span data-ttu-id="cda18-119">Użyj polecenia `openssl version -d` , aby określić katalog główny specyficzny dla platformy, który może się różnić od */etc/SSL/*.</span><span class="sxs-lookup"><span data-stu-id="cda18-119">Use the command `openssl version -d` to determine the platform-specific root, which may differ from */etc/ssl/*.</span></span> <span data-ttu-id="cda18-120">Na przykład w systemie Ubuntu 18,04 katalog jest */usr/lib/SSL/certs/* , a plik jest */usr/lib/SSL/cert.pem*.</span><span class="sxs-lookup"><span data-stu-id="cda18-120">For example, on Ubuntu 18.04, the directory is */usr/lib/ssl/certs/* and the file is */usr/lib/ssl/cert.pem*.</span></span> <span data-ttu-id="cda18-121">Jednak */usr/lib/SSL/certs/* jest link symboliczny do */etc/SSL/certs/* i */usr/lib/SSL/cert.pem* nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="cda18-121">However, */usr/lib/ssl/certs/* is a symlink to */etc/ssl/certs/* and */usr/lib/ssl/cert.pem* does not exist.</span></span>

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

### <a name="category"></a><span data-ttu-id="cda18-122">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cda18-122">Category</span></span>

<span data-ttu-id="cda18-123">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="cda18-123">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="cda18-124">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cda18-124">Affected APIs</span></span>

- <xref:System.Security.Cryptography.X509Certificates.X509Chain?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Security.Cryptography.X509Certificates.X509Chain`

-->
