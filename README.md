# Postfix-remove

Search a postfix queue for messages and delete them. A bit like a Postfix analog
to `qmail-remove`

# Usage

For example:

   postfix-remove --from bill@microsoft.com --delete

Options for matching the message are:

    -f --from [pattern]      Select emails whose from address matches <pattern>
    -t --to [pattern]        Select emails whose to address matches <pattern>
    -r --reason [pattern]    Select emails whose reason for deferral matches <pattern>

Where 'reason' is essentially the string given in `postqueue -p`.

Matching is 'or' based, so adding more checks will delete *more* mail, not a smaller, 
more specific subset.

Patterns are perl regexes. ".com" will match any character followed by the three
characters 'c', 'o', and 'm', but "\.com$" will only match those addresses ending
with '.com'. Marching is case-insensitive.


