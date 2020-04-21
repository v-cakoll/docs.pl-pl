---
title: Rozpoczynanie pracy z usługą Azure File Storage przy użyciu języka F#
description: Usługa Magazyn plików Azure umożliwia przechowywanie plików danych w chmurze oraz instalowanie udziału plików w chmurze z maszyny wirtualnej platformy Azure lub z aplikacji lokalnych działających w systemie Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739590"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Wprowadzenie do usługi Azure File Storage przy użyciu języka F\#

Azure File Storage to usługa, która umożliwia korzystanie z udziałów plików w chmurze przy użyciu standardowego [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Obsługiwane są wersje 2.1 i 3.0 protokołu SMB. W usłudze Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania. Aplikacje uruchomione na maszynach wirtualnych lub w ramach usług w chmurze platformy Azure, a także na klientach lokalnych mogą instalować udziały plików w chmurze tak samo jak aplikacja na komputerze instalująca typowy udział SMB. Dowolna liczba składników aplikacji może następnie równocześnie zainstalować udział Magazynu plików i uzyskiwać do niego dostęp.

Aby uzyskać koncepcyjny przegląd przechowywania plików, zobacz [przewodnik .NET dotyczący przechowywania plików](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Wymagania wstępne

Aby skorzystać z tego przewodnika, należy najpierw [utworzyć konto magazynu platformy Azure](https://docs.microsoft.com/azure/storage/storage-create-storage-account).
Będziesz również potrzebować klucza dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie skryptu języka F# i interakcyjny startu języka F#

Przykłady w tym artykule mogą być używane w aplikacji Języka F# lub skryptu F#. Aby utworzyć skrypt F#, należy `.fsx` utworzyć plik `files.fsx`z rozszerzeniem, na przykład w środowisku deweloperskim Języka F#.

Następnie użyj [menedżera pakietów,](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub `WindowsAzure.Storage.dll` [NuGet](https://www.nuget.org/) zainstalować `WindowsAzure.Storage` pakiet i odwołanie w skrypcie przy użyciu `#r` dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujące instrukcje `open` na początku pliku `files.fsx`:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobieranie parametrów połączenia

Będziesz potrzebować ciągu połączenia usługi Azure Storage dla tego samouczka. Aby uzyskać więcej informacji na temat ciągów połączeń, zobacz [Konfigurowanie ciągów połączeń magazynu](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).

W samouczku wprowadzisz parametry połączenia w skrypcie, w ten sposób:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Nie jest to jednak **zalecane** w przypadku rzeczywistych projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze chroń klucz konta magazynu. Nie udostępniaj go innym użytkownikom, nie koduj go trwale ani nie zapisuj w zwykłym pliku tekstowym, do którego mają dostęp inne osoby. Można ponownie wygenerować klucz przy użyciu witryny Azure portal, jeśli uważasz, że może to być zagrożone.

W przypadku rzeczywistych aplikacji najlepszym sposobem utrzymania ciągu połączenia magazynu jest plik konfiguracyjny. Aby pobrać ciąg połączenia z pliku konfiguracyjnego, można to zrobić:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takiego jak `ConfigurationManager` typ programu .NET Framework.

### <a name="parse-the-connection-string"></a>Analizowanie parametrów połączenia

Aby przeanalizować parametry połączenia, należy użyć:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Spowoduje to `CloudStorageAccount`zwrócenie .

### <a name="create-the-file-service-client"></a>Tworzenie klienta usługi plików

Typ `CloudFileClient` umożliwia programowe korzystanie z plików przechowywanych w magazynie plików. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane i zapisuje dane do magazynu plików.

## <a name="create-a-file-share"></a>Tworzenie udziału plików

W tym przykładzie pokazano, jak utworzyć udział plików, jeśli jeszcze nie istnieje:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Tworzenie katalogu głównego i podkatalogu

W tym miejscu otrzymasz katalog główny i otrzymujesz podkatalog katalogu głównego. Można utworzyć zarówno, jeśli jeszcze nie istnieją.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Przekazywanie tekstu jako pliku

W tym przykładzie pokazano, jak przekazać tekst jako plik.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Pobieranie pliku do lokalnej kopii pliku

W tym miejscu można pobrać plik właśnie utworzony, dołączając zawartość do pliku lokalnego.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Ustawianie maksymalnego rozmiaru udziału plików

W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału w udziale. `FetchAttributes`należy wywołać, aby wypełnić `Properties`udział `SetProperties` i propagować lokalne zmiany w usłudze Azure File Storage.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików

Można wygenerować sygnaturę dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku. Można też utworzyć zasady dostępu współdzielonego w udziale plików na potrzeby zarządzania sygnaturami dostępu współdzielonego. Utworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie sygnatur w przypadku zagrożenia bezpieczeństwa.

W tym miejscu należy utworzyć zasady dostępu współdzielonego w udziale, a następnie użyć tej zasady, aby zapewnić ograniczenia dotyczące sygnatury dostępu Współdzielonego w pliku w udziale.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [Using Shared Access Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) (Używanie sygnatur dostępu współdzielonego (SAS)) oraz [Create and use a SAS with Blob storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2) (Tworzenie i używanie sygnatury dostępu współdzielonego w Magazynie obiektów Blob).

### <a name="copy-files"></a>Kopiowanie plików

Plik można skopiować do innego pliku lub obiektu blob lub obiektu blob do pliku. W przypadku kopiowania obiektu blob do pliku lub pliku do obiektu blob *należy* użyć podpisu dostępu współdzielonego (SAS) do uwierzytelnienia obiektu źródłowego, nawet jeśli kopiujesz w ramach tego samego konta magazynu.

### <a name="copy-a-file-to-another-file"></a>Kopiowanie pliku do innego pliku

W tym miejscu można skopiować plik do innego pliku w tym samym udziale. Ponieważ ta operacja kopiowania jest wykonywana w ramach tego samego konta magazynu, można użyć uwierzytelniania przy użyciu klucza wspólnego.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopiowanie pliku do obiektu blob

W tym miejscu należy utworzyć plik i skopiować go do obiektu blob w ramach tego samego konta magazynu. Sygnatury dostępu Współdzielonego dla pliku źródłowego, którego usługa używa do uwierzytelniania dostępu do pliku źródłowego podczas operacji kopiowania.

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

W ten sam sposób można skopiować obiekt blob do pliku. Jeśli obiekt źródłowy jest obiektem blob, utwórz sygnaturę dostępu współdzielonego w celu uwierzytelniania dostępu do tego obiektu blob podczas operacji kopiowania.

## <a name="troubleshooting-file-storage-using-metrics"></a>Rozwiązywanie problemów z usługą Magazyn plików przy użyciu metryk

Usługa Azure Storage Analytics obsługuje metryki magazynu plików. Dane metryk umożliwiają śledzenie żądań i diagnozowanie problemów.

Można włączyć metryki magazynu plików z [witryny Azure portal](https://portal.azure.com), lub można to zrobić z języka F# w ten sposób:

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji na temat usługi Azure File Storage, zobacz te łącza.

### <a name="conceptual-articles-and-videos"></a>Artykuły koncepcyjne i filmy

- [Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/) (Azure File Storage: płynnie działający system plików SMB w chmurze dla systemów Windows i Linux)
- [Jak korzystać z usługi Azure File Storage z systemem Linux](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Narzędzia dostępne dla usługi Magazyn plików

- [Używanie programu Azure PowerShell z usługą Azure Storage](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [How to use AzCopy with Microsoft Azure Storage (Jak używać narzędzia AzCopy z usługą Magazyn Microsoft Azure)](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [Tworzenie, pobieranie i wyświetlanie listy obiektów blob za pomocą interfejsu wiersza polecenia platformy Azure](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a>Tematy pomocy

- [Biblioteka klienta magazynu dla odwołania .NET](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dokumentacja interfejsu API REST usługi plików](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Wpisy na blogach

- [Azure File storage is now generally available (Usługa Magazyn plików Azure została udostępniona publicznie)](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) (Za kulisami usługi Azure File Storage)
- [Introducing Microsoft Azure File Service](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service) (Wprowadzenie do usługi plików platformy Microsoft Azure)
- [Persisting connections to Microsoft Azure Files (Utrwalanie połączeń z plikami na platformie Microsoft Azure)](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
