---
title: Podstawowe zmiany w bibliotece klas podstawowych
description: Wyświetla istotne zmiany w podstawowych bibliotekach programu .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365622"
---
# <a name="core-net-libraries-breaking-changes"></a>Podstawowe zmiany w bibliotekach .NET

Podstawowe biblioteki .NET zapewniają pierwotne i inne typy ogólne używane przez platformę .NET Core.

Następujące istotne zmiany zostały udokumentowane na tej stronie:

| Zmiana podziału | Wprowadzona wersja |
| - | :-: |
| [Metody SSE i SSE2 CompareGreaterThan prawidłowo obsługują dane wejściowe NaN](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [Element CounterSet. CreateCounterSetInstance teraz zgłasza InvalidOperationException, jeśli wystąpienie już istnieje](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [Usunięto pakiet Microsoft. DotNet. PlatformAbstractions](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
| [Interfejsy API służące do raportowania wersji teraz produktu i nie wersji](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Niestandardowe wystąpienia EncoderFallbackBuffer nie mogą podlegać rekursywnie](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Zmiany zachowań formatowania zmiennoprzecinkowego i analizowania](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Operacje analizowania zmiennoprzecinkowe nie będą już kończyć się niepowodzeniem lub nie generują wyjątku overflow](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException — przeniesiony do innego zestawu](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Zastępowanie źle sformułowanych sekwencji bajtów w formacie UTF-8 następuje po wskazówkach dotyczących standardu Unicode](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute przeniesiony do innego zestawu](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [Element ZipArchiveEntry nie obsługuje już archiwów z niespójnymi rozmiarami wpisów](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [Typ wyjątku serializatora JSON został zmieniony z elementu Jsonexception na NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Zmień semantykę (String) na wartość null w Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Metody JsonEncodedText. Encode mają dodatkowy argument JavaScriptEncoder](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [Zmieniono sygnaturę JsonFactoryConverter. isconverter](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Zmiany interfejsu API jsonelement](#jsonelement-api-changes) | 3.0 |
| [Element FieldInfo. SetValue zgłasza wyjątek dla pól static, tylko init](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Pola prywatne dodane do wbudowanych typów struktur](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Zmień wartość domyślną UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Wersje OpenSSL na macOS](#openssl-versions-on-macos) | 2.1 |
| [UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [Właściwości UriBuilder nie dołączają już znaków wiodących](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [Proces. element StartInfo zgłasza InvalidOperationException dla procesów, które nie zostały uruchomione](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
