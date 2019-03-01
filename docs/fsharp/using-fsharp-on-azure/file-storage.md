---
title: Rozpoczynanie pracy z usługą Azure File storage przy użyciuF#
description: Store danych plików w chmurze za pomocą usługi Azure File storage i instalowanie udziału plików w chmurze z maszyny wirtualnej (VM) platformy Azure lub z aplikacji w środowisku lokalnym systemem Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: fa6dadc863bb9116cfac5afd7cd22a724bc7afe2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969599"
---
# <a name="get-started-with-azure-file-storage-using-f"></a>Rozpoczynanie pracy z usługą Azure File storage przy użyciu F\#

Usługa Azure File storage to usługa, która oferuje udziały plików w chmurze przy użyciu standardowych [protokołu bloku komunikatów serwera (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx). Obsługiwane są wersje 2.1 i 3.0 protokołu SMB. W usłudze Magazyn plików Azure można migrować starsze aplikacje korzystające z udziałów plików na platformę Azure szybko i bez kosztownych modyfikacji oprogramowania. Aplikacje uruchomione na maszynach wirtualnych lub w ramach usług w chmurze platformy Azure, a także na klientach lokalnych mogą instalować udziały plików w chmurze tak samo jak aplikacja na komputerze instalująca typowy udział SMB. Dowolna liczba składników aplikacji może następnie równocześnie zainstalować udział Magazynu plików i uzyskiwać do niego dostęp.

Omówienie usługi file storage można znaleźć [przewodnik platformy .NET dla usługi file storage](/azure/storage/storage-dotnet-how-to-use-files).

## <a name="prerequisites"></a>Wymagania wstępne

Aby użyć tego przewodnika, należy najpierw [Tworzenie konta usługi Azure storage](/azure/storage/storage-create-storage-account).
Należy także klucz dostępu do magazynu dla tego konta.

## <a name="create-an-f-script-and-start-f-interactive"></a>Tworzenie F# skrypt i uruchomić F# interaktywne

Przykłady w tym artykule mogą być używane w jednej F# aplikacji lub F# skryptu. Aby utworzyć F# skrypt, Utwórz plik o `.fsx` rozszerzenia, na przykład `files.fsx`w usługi F# środowiska deweloperskiego.

Następnie użyj [Menedżera pakietów](package-management.md) takich jak [Paket](https://fsprojects.github.io/Paket/) lub [NuGet](https://www.nuget.org/) zainstalował `WindowsAzure.Storage` pakietów i odwołań `WindowsAzure.Storage.dll` w skrypcie za pomocą `#r`dyrektywy.

### <a name="add-namespace-declarations"></a>Dodawanie deklaracji przestrzeni nazw

Dodaj następujący kod `open` instrukcji na górze `files.fsx` pliku:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a>Pobieranie parametrów połączenia

Na potrzeby tego samouczka konieczne będzie parametrów połączenia usługi Azure Storage. Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz [skonfigurować parametry połączenia magazynu](/azure/storage/storage-configure-connection-string).

Samouczek wprowadzisz parametrów połączenia w skrypcie w następujący sposób:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

Jest to jednak **niezalecane** rzeczywiste projektów. Klucz konta magazynu jest podobny do hasła głównego konta magazynu. Zawsze starannie Chroń klucz konta magazynu. Należy unikać, ich dystrybucję w innym użytkownikom, kodować je lub zapisanie go w pliku tekstowego, który jest dostępny dla innych użytkowników. Można ponownie wygenerować klucz za pośrednictwem witryny Azure Portal, jeśli uważasz, że mogą zostać przejęte.

Rzeczywiste aplikacje najlepiej przechowywać parametry połączenia magazynu jest w pliku konfiguracji. Aby pobrać parametry połączenia z pliku konfiguracji, można to zrobić:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

Użycie programu Azure Configuration Manager jest opcjonalne. Można również użyć interfejsu API, takich jak .NET Framework `ConfigurationManager` typu.

### <a name="parse-the-connection-string"></a>Przeanalizować parametrów połączenia

Aby przeanalizować parametrów połączenia, należy użyć:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

Spowoduje to zwrócenie `CloudStorageAccount`.

### <a name="create-the-file-service-client"></a>Tworzenie klienta usługi plików

`CloudFileClient` Typu umożliwia programowe używanie plików przechowywanych w usłudze File storage. Oto jeden ze sposobów tworzenia klienta usługi:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

Teraz możesz przystąpić do pisania kodu, który odczytuje dane z i zapisuje dane do magazynu plików.

## <a name="create-a-file-share"></a>Utwórz udział plików

W tym przykładzie pokazano, jak utworzyć udział plików, jeśli jeszcze nie istnieje:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a>Utwórz katalog główny i to podkatalog

W tym miejscu otrzymasz katalog główny i pobrać podrzędnych katalogu głównego. Możesz utworzyć obie Jeśli jeszcze nie istnieją.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a>Prześlij tekst jako plik

Ten przykład przedstawia sposób przekazywania tekst w formacie.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a>Pobierz plik w lokalnej kopii pliku

Tutaj możesz pobrać plik, który został właśnie utworzony, dołącza zawartość do pliku lokalnego.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a>Ustaw maksymalny rozmiar udziału plików

W poniższym przykładzie pokazano, jak sprawdzić bieżące użycie udziału oraz jak ustawić limit przydziału dla udziału. `FetchAttributes` musi zostać wywołana w celu wypełnienia udziału `Properties`, i `SetProperties` propagowanie zmian lokalnych do usługi Azure File storage.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a>Generowanie sygnatury dostępu współdzielonego dla pliku lub udziału plików

Można wygenerować sygnatury dostępu współdzielonego (SAS) dla udziału plików lub dla pojedynczego pliku. Można również utworzyć zasady dostępu współdzielonego w udziale plików, aby zarządzać sygnatur dostępu współdzielonego. Tworzenie zasad dostępu współdzielonego jest zalecane, ponieważ umożliwia cofnięcie Sygnatur w przypadku powinien być naruszenia zabezpieczeń.

W tym miejscu tworzysz wspólny dostęp do zasad w udziale, a następnie użyć tych zasad nakładane są ograniczenia na sygnatury dostępu Współdzielonego dla pliku w udziale.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

Aby uzyskać więcej informacji na temat tworzenia i używania sygnatur dostępu współdzielonego, zobacz [za pomocą sygnatur dostępu udostępnionego (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) i [tworzenia i używania sygnatur dostępu Współdzielonego z usługą Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).

### <a name="copy-files"></a>Kopiowanie plików

Można skopiować pliku do innego pliku lub do obiektu blob oraz obiekty blob do pliku. Podczas kopiowania obiektu blob do pliku lub pliku do obiektu blob, możesz *musi* używają sygnatury dostępu współdzielonego (SAS) do uwierzytelniania obiektu źródłowego, nawet wtedy, gdy są kopiowane w ramach tego samego konta magazynu.

### <a name="copy-a-file-to-another-file"></a>Kopiowanie pliku do innego pliku

W tym miejscu można skopiować pliku do innego pliku w tym samym udziale. Ponieważ ta operacja kopiowania kopiuje między plikami na tym samym koncie magazynu, można użyć uwierzytelniania klucza wspólnego, do wykonania kopii.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a>Kopiowanie pliku do obiektu blob

W tym miejscu należy utworzyć plik i skopiuj go do obiektu blob w ramach tego samego konta magazynu. Możesz utworzyć sygnaturę dostępu Współdzielonego dla pliku źródłowego, w której usługa uwierzytelniania dostępu do pliku źródłowego podczas operacji kopiowania.

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

W ten sam sposób, można skopiować obiektu blob do pliku. Jeśli obiekt źródłowy jest obiektem blob, Utwórz sygnaturę dostępu Współdzielonego w celu uwierzytelnienia dostępu do tego obiektu blob podczas operacji kopiowania.

## <a name="troubleshooting-file-storage-using-metrics"></a>Rozwiązywanie problemów z magazynem plików przy użyciu metryk

Analizy usługi Azure Storage obsługuje metryki dla usługi File storage. Dane metryk można Śledzenie żądań i diagnozowanie problemów.

Możesz włączyć metryki dla usługi File storage z [witryny Azure Portal](https://portal.azure.com), lub możesz to zrobić z F# następująco:

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a>Następne kroki

Zobacz te linki, aby uzyskać więcej informacji na temat usługi Azure File storage.

### <a name="conceptual-articles-and-videos"></a>Artykuły koncepcyjne i filmy

- [Usługa Azure Files Storage: frictionless cloud SMB file system for plików Windows i Linux](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [Jak używać usługi Azure File Storage z systemem Linux](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a>Narzędzia do obsługi dla usługi File storage

- [Używanie programu Azure PowerShell z usługą Azure Storage](/azure/storage/storage-powershell-guide-full)
- [Jak używać narzędzia AzCopy z usługą Microsoft Azure Storage](/azure/storage/storage-use-azcopy)
- [Przy użyciu wiersza polecenia platformy Azure z usługą Azure Storage](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a>Tematy pomocy

- [Biblioteka klienta usługi Storage dla platformy .NET odwołania](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [Dokumentacja interfejsu API REST usługi plików](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a>Wpisy w blogu

- [Usługa Azure File storage jest teraz ogólnie dostępna](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [Inside Azure File Storage](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [Wprowadzenie do usługi Microsoft Azure File Service](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [Persisting Connections to Microsoft Azure Files połączeń](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
