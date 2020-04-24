---
title: Serializacja binarna
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400639"
---
# <a name="binary-serialization"></a>Serializacja binarna

Serializacja mogą być definiowane jako proces przechowywania stanu obiektu na nośniku. W trakcie tego procesu publiczny i prywatny pola obiektu oraz nazwę klasy, łącznie z zestawu zawierającego klasy, są konwertowane na strumień bajtów, które są następnie zapisywane do strumienia danych. Gdy obiekt jest następnie przeprowadzona, dokładną oryginalnego obiektu zostanie utworzony.

W przypadku implementowania mechanizmu serializacji w środowisku zorientowanym obiektowo trzeba zwiększyć liczbę kompromisów między łatwośćmi użytkowania i elastyczność. Ten proces można automatycznego w dużym stopniu, pod warunkiem, że podane są wystarczające kontrolę nad procesem. Mogą na przykład wystąpić sytuacje, w których prosta Serializacja binarna nie jest wystarczająca lub może istnieć specyficzny powód, aby określić, które pola w klasie muszą być serializowane. W poniższych sekcjach opisano niezawodny mechanizm serializacji zapewniany z platformą .NET oraz kilka ważnych funkcji, które umożliwiają dostosowanie procesu do własnych potrzeb.

> [!NOTE]
> Stan UTF-8 lub UTF-7 kodowany obiektu nie jest zachowana, jeśli obiekt jest serializacji i deserializacji za pomocą różnych wersji programu .NET Framework.

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

Serializacja binarna pozwala modyfikować prywatne elementy członkowskie wewnątrz obiektu i w związku z tym zmieniać jego stan. Z tego względu zalecane są inne platformy serializacji, <xref:System.Text.Json?displayProperty=fullName>takie jak, które działają na publicznej powierzchni interfejsu API.

## <a name="net-core"></a>.NET Core

Platforma .NET Core obsługuje serializację binarne dla podzbioru typów. Listę obsługiwanych typów można zobaczyć w poniższej sekcji [typy serializowane](#serializable-types) . Wymienione typy są gwarantowane do serializacji między .NET Framework 4.5.1 i nowszymi wersjami oraz między programem .NET Core 2,0 i jego nowszymi wersjami. Inne implementacje platformy .NET, takie jak mono, nie są oficjalnie obsługiwane, ale również powinny funkcjonować.

### <a name="serializable-types"></a>Typy możliwe do serializacji

> [!div class="mx-tdCol2BreakAll"]
> | Typ | Uwagi |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.AggregateException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4.<br/>Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana. |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DBNull?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.2 i nowszych wersji. |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | Jeśli ustawisz `RemotingFormat` wartość `SerializationFormat.Binary`, może ona być wymieniana tylko z platformą .NET Core 2,1 i nowszymi wersjami. |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4.<br/>Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.6. |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.FormatException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.OverflowException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.RankException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4.<br/>Serializacja z .NET Framework do platformy .NET Core nie jest obsługiwana. |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4.<br/>Ograniczone dane serializacji. |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | Nie można serializować w .NET Framework 4,7 i wcześniejszych wersjach. |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | Począwszy od platformy .NET Core 2.0.4. |

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.Serialization>\
Zawiera klasy, które mogą być używane do serializacji i deserializacji obiektów.

- [Serializacja XML i SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md)\
Opisuje mechanizm serializacji XML, który jest dołączony do aparatu PLików wykonywalnych języka wspólnego.

- [Zabezpieczenia i Serializacja](../../../docs/framework/misc/security-and-serialization.md)\
Opisuje bezpiecznego wskazówek kodowania, które należy wykonać podczas pisania kodu, który będzie wykonywać serializacji.

- [Komunikacja zdalna .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
Opisuje różne metody, które są uruchamiane w .NET Framework na potrzeby komunikacji zdalnej.

- [Usługi sieci Web XML utworzone za pomocą ASP.NET i klientów usług sieci Web XML](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
Artykuły opisujące i objaśniające sposób programowania usług sieci Web XML utworzonych za pomocą ASP.NET.
