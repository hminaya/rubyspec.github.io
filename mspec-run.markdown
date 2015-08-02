---
layout: page
---

## mspec-run

Once the [mspec]({{ site.baseurl }}/mspec/) options are processed, the designated target is executed with the remaining options. The general purpose spec runner, `bin/mspec-run`, accepts a file, directory, or shell glob to specify which spec files to execute. It has the following options:

<pre>
$ bin/mspec run -h
ruby 1.8.6 (2008-03-03 patchlevel 114) [universal-darwin9.0]
mspec run [options] (FILE|DIRECTORY|GLOB)+

 Ask yourself:
  1. What specs to run?
  2. How to modify the execution?
  3. How to display the output?
  4. What action to perform?
  5. When to perform it?

 What specs to run
   -e, --example STR          Run examples with descriptions matching STR
   -E, --exclude STR          Exclude examples with descriptions matching STR
   -p, --pattern PATTERN      Run examples with descriptions matching PATTERN
   -P, --excl-pattern PATTERN Exclude examples with descriptions matching PATTERN
   -g, --tag TAG              Run examples with descriptions matching ones tagged with TAG
   -G, --excl-tag TAG         Exclude examples with descriptions matching ones tagged with TAG
   -w, --profile FILE         Run examples for methods listed in the profile FILE
   -W, --excl-profile FILE    Exclude examples for methods listed in the profile FILE

 How to modify the execution
   -B, --config FILE          Load FILE containing configuration options
   -n, --name RUBY_NAME       Set the value of RUBY_NAME (used to determine the implementation)
   -H, --random               Randomize the list of spec files
   -Z, --dry-run              Invoke formatters and other actions, but don't execute the specs
       --int-spec             Control-C interrupts the current spec only

 How to display their output
   -f, --format FORMAT        Formatter for reporting, where FORMAT is one of:

       s, spec, specdoc         SpecdocFormatter
       h, html,                 HtmlFormatter
       d, dot, dotted           DottedFormatter
       f, file                  FileFormatter
       u, unit, unitdiff        UnitdiffFormatter
       m, summary               SummaryFormatter
       a, *, spin               SpinnerFormatter
       t, method                MethodFormatter
       y, yaml                  YamlFormatter

   -o, --output FILE          Write formatter output to FILE
   -V, --verbose              Output the name of each file processed
   -m, --marker MARKER        Output MARKER for each file processed

 What action to perform
       --spec-debug           Invoke the debugger when a spec description matches (see -K, -S)
       --spec-gdb             Invoke Gdb when a spec description matches (see -K, -S)
   -Y, --verify               Verify that guarded specs pass and fail as expected
   -O, --report               Report guarded specs

 When to perform it
   -K, --action-tag TAG       Spec descriptions marked with TAG will trigger the specified action
   -S, --action-string STR    Spec descriptions matching STR will trigger the specified action

 Help!
   -v, --version              Show version
   -h, --help                 Show this message

 How might this work in the real world?

   1. To simply run some specs:

     $ mspec path/to/the/specs
     mspec path/to/the_file_spec.rb

   2. To run specs tagged with 'fails':

     $ mspec -g fails path/to/the_file_spec.rb

   3. To start the debugger before the spec matching 'this crashes':

     $ mspec --spec-debug -S 'this crashes' path/to/the_file_spec.rb
</pre>

<code>-f, --format FORMAT</code>

Selects the reporter format to output specs strings and failures. The specdoc formatter is very similar to RSpec's <code>-f s</code> option. The dotted formatter outputs the familiar <code>'....F..EF..''</code> with exceptions listed after all specs are run. The summary formatter only outputs the elapsed time and the tallies for files, examples, failures, and errors. The spinner formatter shows a progress bar. The YAML formatter is useful for automated processing.

<code>-e, --example STRING|FILE</code>

Executes only the specs whose description string matches STRING.

<code>-E, --exclude STRING|FILE</code>

Does not execute any spec whose description string matches STRING.

<code>-p, --pattern PATTERN</code>

Executes only the specs whose description string matches the Regexp PATTERN. Specify the pattern without `//` characters. For example, to execute all specs whose description strings contain _sorts_ or _returns_, use <code>-p '(sorts|returns)'</code>.

<code>-P, --exclude-pattern PATTERN</code>

Does not execute any spec whose description string matches the Regexp PATTERN.

<code>-g, --tag TAG</code>

Executes only the specs whose description string matches one tagged with TAG.

<code>-G, --exclude-tag TAG</code>

Does not execute any spec whose description string matches one tagged with TAG.

<code>-V, --verbose</code>

Outputs the name of each file processed.

<code>-m, --marker MARKER</code>

Outputs MARKER for each file processed. Overrides -V.

