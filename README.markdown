# Purpose

maxframe provides the ability to maximize the emacs frame and stay within
the display resolution.

## Usage

[Autoload comments][1] are provided. If you're installing this via elpa you
shouldn't need to do anything else.

Otherwise, add maxframe.el to your load-path and run some form of
`(autoload 'maximize-frame "maxframe" "Maximize the focussed frame." t)` in
your init.el.

If using two framebuffers (monitors), it might be necesssary to specify a
mf-max-width value set to the pixel width of main framebuffer. This is
necessary because emacs does not yet support sniffing different
framebuffers. Example:

    M-x customize-group RET maxframe RET
    set mf-max-width to 1600 ;; Pixel width of main monitor.

    ;; In init.el
    
    (add-hook 'window-setup-hook 'maximize-frame t)

To restore the frame to it's original dimensions, call restore-frame:

    M-x restore-frame

## How it works

puts the emacs frame in the top left corner of the display and calculates
the maximum number of columns and rows that can fit in the display

## Limitations

Requires Emacs 22 (for fringe support), but maximize-frame still works
under Emacs 21 on Windows.

`maximize-frame` cannot automatically re-maximize when the resolution of
your monitor has changed. However, it should properly maximize the frame if
you manually call `maximize-frame` again. If you know a hook that emacs has
when the display resolution has been changed, let the developers know.

## Credits

The w32 specific functions were borrowed from the Emacs Manual:
http://www.gnu.org/software/emacs/windows/big.html#windows-like-window-ops

[1]: http://www.gnu.org/software/emacs/elisp/html_node/Autoload.html